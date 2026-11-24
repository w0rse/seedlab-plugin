# Seed Lab

Seed Lab is a Claude plugin that redesigns one page in your own codebase, so that it stops looking like the page every agent builds. It holds one skill, `redesign-page`, and one connector, the Seed Lab server.

It is for people who build with Claude in a real project and have a page that works and looks generic: a landing page, a pricing page, a dashboard, a tool. It does not repaint the layout you have. It works out what the page is for and proposes pages that are organised differently.

Three things set it apart from other design skills:

- **The directions come from outside web design.** Each one is built on an object people already know how to read (a timetable, a label, an instrument panel), drawn from a bank of 220, and each has a palette of four colours. No kind of object is offered twice, so the directions differ in what the page is made of and not only in its colours.
- **A second model looks at the result.** Screenshots of the built page go to a design director, a model from another vendor than the one that built it, and its notes come back to be acted on.
- **The wording was chosen by blind votes.** The instructions the page is built and finished from are the ones whose pages were picked in more than two thousand blind votes between pairs of pages, nearly all cast by one person, the project's author. The experiment, its findings and the vote are at https://w0rse.xyz/seedlab/.

## What happens

1. Claude reads your project and the page, and says what the page is for and what is wrong with it. If you have not said what problem you want solved, it asks you once.
2. Seed Lab draws directions, four unless you ask otherwise.
3. Claude builds a quick first screen of each, with your page's real words and figures, and shows them together with the page as it is now.
4. You choose. Claude does not choose for you, and does not merge two directions into one.
5. Claude rebuilds the page in the direction you chose, in the stack your project already uses, keeping everything you said must keep working.
6. Claude sends screenshots to the design director and acts on the notes, for up to three rounds.

The colours of a direction can be shown, redrawn or tuned at any point, before or after the page is built.

## Installing

In Claude Code, add this repository as a marketplace and install the plugin from it:

```bash
claude plugin marketplace add w0rse/seedlab-plugin
```

```bash
claude plugin install seedlab@seedlab
```

Inside a session the same two steps are `/plugin marketplace add w0rse/seedlab-plugin` and `/plugin install seedlab@seedlab`.

To try it for one session without installing anything, from a copy of this repository:

```bash
claude --plugin-dir .
```

There is no sign-in and no key to set.

## Using it

Open Claude in your project and ask in your own words. Three requests it is made for:

- "Redesign the pricing page. It looks like every other pricing page."
- "The dashboard's first screen looks AI-generated. Give me four directions for it and sketch each one, so I can choose."
- "This app has no sign-up page yet. Design one with Seed Lab, and have it reviewed before you call it done."

Things you can say on the way: "three directions, not four"; "further takes on the second one"; "new typefaces as well"; "the colours are dull, redraw them"; "more contrast"; "skip the review".

## What it needs

- A project Claude can read and edit, with the page rendering on your machine. The server cannot reach your machine, so Claude takes the screenshots.
- A way for Claude to take a screenshot of a page: a browser tool, or a headless browser it can run.
- Claude Opus as the building model, if you have the choice. The process was tested with it; see "What was tested".

It was built and tried in Claude Code. It has not yet been tried in Claude's chat apps or in Cowork.

## What is in the plugin

- `skills/redesign-page/SKILL.md`: the process, step by step.
- `skills/redesign-page/references/`: the instructions Claude follows for the sketch, the build and the finishing, as templates; what each further take asks for; and how to change colours on a page that is already built.
- `.mcp.json`: the address of the Seed Lab connector, `https://w0rse.xyz/seedlab/mcp/data`.

Every instruction Claude follows is in these files, where you can read it. The connector returns data only: the objects and colours that were drawn, the values for the object you chose, and the director's notes.

## The connector's tools

| Tool | What it does | What it changes |
| --- | --- | --- |
| `directions` | Draws several directions for a page from what Claude wrote about it. No model is called. | Stores that description on the server. |
| `chosen_object` | Returns the values for one chosen object or take: the object, the colours, the parts that stay plain. | Nothing. |
| `variations` | Draws further takes on one object. | Nothing. |
| `colours` | Shows, redraws or tunes the four colours of a direction. | The colours stored with that direction. |
| `upload_screenshots` | Opens one-time addresses that screenshots are sent to. | Holds a screenshot until it is reviewed. |
| `review` | Passes the screenshots and the description to the design director and returns its notes. | Nothing on the server; the screenshots are deleted. |

## What it sends, and what is kept

The full account is in [PRIVACY.md](PRIVACY.md). In short:

**To the Seed Lab server, when directions are asked for:** what Claude wrote about your page: the product, the audience, the kind of page, what people come to it to do, the problem to solve, what must keep working, and a short description of what is on the page. This is kept on the server as a small file for 30 days after it was last used, so that later calls can refer to a direction by its id, and is then deleted. Do not let secrets or private data into that description.

**To the Seed Lab server, when a review is asked for:** up to 6 screenshots of the page, each at most 2 MB, sent to one-time addresses the server gives out. A screenshot waits there for at most 30 minutes and is deleted once the director has answered.

**To another company's model, when a review is asked for:** the screenshots and the description above go to the design director, a model from a vendor other than Anthropic (by default `openai/gpt-6.1-terra`), through OpenRouter. Claude is told to say so before the first review. If a page shows anything that must not leave your machine, do not have it reviewed; everything else works without a review.

**To Google, only if you ask for typefaces:** the build instruction then names two typefaces from Google Fonts, and the page it builds will load them from there.

The plugin fetches nothing else and runs nothing on your machine. It keeps nothing on your machine either; Claude writes its sketches into your project, in a `sketches` folder.

## Sign-in and limits

There is no sign-in and no account. The server tells callers apart only to apply its limits, by a salted hash of the address a request comes from; the hash is written to the connector's log with the time and the name of the tool called, and the address is not. The web server in front of the connector keeps an access log of its own, which records addresses, for about a week.

The limits for one caller are 120 requests a minute, 30 reviews an hour and 40 a day. Reviews cost money, so there is also a budget for everyone together, 300 a day by default; when it is spent, a review answers that it was not made, and the rest goes on working.

## When something goes wrong

- **Claude says the Seed Lab connector is not connected.** The six tools are missing from the session. In Claude Code, `/mcp` shows whether the `seedlab` server answered; in Claude's apps, connect it on the plugin's Connectors tab. If it is connected and does not answer, the server is down: please open an issue.
- **A review "was not made".** The answer says why: a limit was reached, the day's budget for everyone is spent, or the director could not be reached. The budget starts again at midnight UTC. The page can be finished without a review, from the finishing instruction alone.
- **An id is not one the server knows.** Directions are deleted 30 days after they were last used. Ask for directions again; the same request with the same seed returns the same draw.
- **A screenshot is refused.** It is over 2 MB, is not a PNG, JPEG or WebP image, or its address was used already or is older than 30 minutes. Ask for new addresses.
- **None of the objects suits the page.** Claude is told to say so and leave that direction out. Ask for another draw.
- **The colours are wrong for you.** Ask for them to be redrawn or tuned; the page does not have to be rebuilt for that.

## What was tested

The numbered direction in the build instruction, the finishing instruction and the director's prompt are the texts pages were built from and that people voted on in the experiment. Everything written around them for work in a real project has not been through a vote: the steps of the skill, the rules about a project's own stack, the sketch instruction, what is said about pages people operate, and the rule to define the four colours once. The build instruction says which is which.

The process was tested with Claude Opus as the building model. Sonnet, under the same instructions, took the borrowed object too far and was picked less often.

The plugin itself has been run end to end in Claude Code on a dashboard, and the same process, through an earlier form of the connector, rebuilt the front page of a live product.

## Questions and faults

Open an issue at https://github.com/w0rse/seedlab-plugin/issues. Issues are public: do not put private data, or screenshots of pages that are not public, into one.
