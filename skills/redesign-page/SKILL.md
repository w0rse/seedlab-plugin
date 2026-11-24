---
name: redesign-page
description: "Redesign a web page in the user's own project with Seed Lab. It works out what the page is for and what is wrong with it, gets several directions that organise the page differently (each built on an object from outside web design, with a set palette), sketches them for the user to choose from, rebuilds the page in the chosen direction, and finishes it with a design director's notes on screenshots. Use when the user asks to redesign, rethink or restyle a page, a screen or a landing page; says a page looks generic, templated, machine-made, AI-generated or like AI slop; or asks for design directions, alternatives or a design review of a page, whether the page exists already or not. Not for small CSS fixes or for building features."
---

# Redesign a page with Seed Lab

Seed Lab is a designer brought into the user's project to redesign one page. Its job is the one a good designer does on arriving: work out what the page is for and what is wrong with it, and propose pages that are organised differently to solve that. It does not offer the layout the page has now in new colours and type.

You do the reading and the building, in the project's existing stack and with its real content. The Seed Lab connector, which is the MCP server named `seedlab` that comes with this plugin, does two things: it draws directions, and it passes screenshots to a design director and returns the notes. It writes no code and sees no files, and what it returns is data. Everything you are asked to do is written here and in the files under `references/`.

## The connector's tools

There are six, referred to below by their plain names. In your list of tools each name carries a prefix for the plugin and the server; they are the tools of the `seedlab` server whose names end in:

- `directions`: draws several directions for a page.
- `chosen_object`: returns the values for one chosen object or take.
- `variations`: draws further takes on one object.
- `colours`: shows, redraws or tunes the colours of a direction.
- `upload_screenshots`: opens one-time addresses for screenshots.
- `review`: sends screenshots to the design director and returns the notes.

If these tools are not there, tell the user that the Seed Lab connector is not connected, and stop. Do not make up directions in its place.

What leaves the user's machine: what you pass to `directions` is kept on the Seed Lab server for 30 days, and screenshots passed to `review` go, with that description, to a model from another vendor through OpenRouter. Say so to the user once, before the first `review`, and do not send screens that show secrets or private data.

## 1. Read before you call anything

Read how the project is built, read the page's code, and look at the page as it renders: take a screenshot at 1440 wide and keep it as the "before". From that, write down what people come to this page to do, what is wrong with it now, and what must keep working.

If the user has not said what problem they want solved, ask them one question and use their words; do not guess it. For a page that does not exist yet, the problem is what the user asked the page to do.

## 2. Ask for directions

Call `directions` with what you found.

- `product`, `audience`: what the product is and who the page is for, a sentence or two each.
- `page_type`: what the page is, not where it sits: "interactive data map", "pricing page", "API reference". "Home page" or "index" says nothing about it.
- `purpose`: what people come to this page to do, as you found it.
- `problem`: the problem the user wants solved, in their own words first, with what you saw is wrong added after.
- `keep`: what must keep working on an existing page: its controls, states, links, data, anything the user said not to lose.
- `working_part`: if the page's main content is a working thing people operate (a map, a chart, a table, an editor, a form), name it in a few words. If there are several, put first the one people come for. Leave it out for a page that is only read.
- `description`: what the page has on it now, or has to have: its sections and its real content, in short. With the fields above, this is all the design director will know about the page.
- `register`: how much design this page can carry, judged by you from how the page is used: 1 is a page people work from (reference, settings, a form, a table of records, a tool operated daily), 5 a page made to be noticed. Leave it out only if you cannot tell.
- `count`: how many directions; 4 unless the user asked otherwise. With 3 or fewer, the three objects of a direction are of three different kinds.
- `seed`: leave it out for a fresh draw. The same call with the same seed returns the same directions.
- `typefaces`: leave it off unless the project may load third-party fonts and the user wants new type.
- `with_tradition`: off unless the user asks for a tradition of graphic design to be drawn as well.

The answer has, for each direction, its id, its four colours, and three candidate objects from outside web design, each with what it would make of this page. No kind of object is offered in two directions, so whichever you choose, the directions differ in what the page is made of and not in its colours. The answer also says how much design the page can carry and which parts of it stay plain whatever the object.

## 3. Choose one object in each direction

Choose one of the three objects in each direction, now that you have read the project. The rule, in the wording that was tested:

> Choose the one that suits this client: the object whose job, whose readers and whose way of ordering things come closest to what this page is for. Suit is not likeness and it is not safety: do not pick an object because it pictures the subject, and do not pick the tamest.

For each direction: Name the one you choose, and say in one sentence why its job, its readers and its way of ordering things suit this client better than the other two. Add what the object would change about the problem. Tell the user every choice and its reason, in two or three sentences each, before you sketch.

If none of a direction's three objects suits this client, say so and leave that direction out. If most directions have none, call `directions` again with another seed.

A chosen object's id is the direction's id with the object's letter: `abcdefgh-2b` is object b of direction `abcdefgh-2`.

## 4. Sketch each chosen object

For each chosen id, call `chosen_object` and follow `references/sketch.md`, filled with the values it returns (see "Reading the reference files" below). A sketch is the first screen only, in a file of its own, with the page's real words and figures.

When every direction has a sketch, show them to the user together, each under its id and its object, with the page as it is now beside them. Where you cannot show pictures, give the paths of the screenshots, or put them on one page the user can open.

## 5. The user chooses

The choice among the sketches is the user's. Do not pick for them, and do not merge two directions into one.

## 6. Further takes, if the user wants them

`variations` returns further takes on the object the user prefers: the object and the colours stay, and what changes is which of the object's properties carries the page. Each take has an id of its own, such as `abcdefgh-2b-scale`, which `chosen_object` and `review` accept. What a take asks for is written in `references/takes.md`. Sketch each take as in step 4 and show them beside the sketch the user already preferred.

## 7. Build the page

Before building, know whether the page's copy may be cut to about half or every word has to stay; ask the user if you do not know. That is `cut_copy` in the build instruction.

Call `chosen_object` again with the id the user chose, since the colours may have been changed since the sketch, and follow `references/build.md`, filled with its values. It is a redesign of the page and not a repaint, written for editing a real project in its existing stack.

## 8. Finish the page, and have it reviewed

When the whole page renders, follow `references/finish.md`, filled the same way. Then have it reviewed, for up to three rounds:

1. Take screenshots of the page as it renders, 1440 wide, one screen per picture from the top, at most 6, each at most 2 MB (JPEG is best). The server cannot reach your localhost, so you take them.
2. Call `upload_screenshots` with how many there are. It returns an address for each. Send one file to each, in order from the top of the page: `curl -sS -X POST --data-binary @screen-1.jpg <address>`. An address takes one picture, once, within 30 minutes; anyone who has it can fill it, so do not paste it into anything shared.
3. Call `review` with the id the page was built from and the upload ids in the same order.

Reading the answer of `review`:

- **Notes.** They are the design director's, and they come with this: "The design director has looked at the page as it renders now; the pictures attached are what was seen. The idea and the page's boldest element stay as they are. Act on each of these notes, and change nothing else:" When these are done, take new screenshots and call `review` again. Three rounds were used in the experiment; stop earlier if the director would let it go live.
- **No notes.** "The design director has looked at the page as it renders now; the pictures attached are what was seen, and would let it go live. Check it once at a phone width and against the acceptance criteria."
- **Not reviewed.** The answer says why: the server has no key for the director's model, a limit was reached, or the director could not be reached. Nothing was wrong with your call. Go on from the finishing instruction alone, looking at your own screenshots as it says; if the director could not be reached, try once more in a minute.

## The colours, at any point

Every direction comes with four colours. `colours` shows, redraws or tunes them, before or after the page is built; see `references/colours.md`.

## Reading the reference files

`references/sketch.md`, `references/build.md` and `references/finish.md` each hold one instruction as a template. The texts in them are the ones pages were built from, and their wording was tested; fill them as follows and then do what they say.

- `{name}` stands for the value called `name` in the answer of `chosen_object`. The one exception is `{take_text}`: it is the paragraph in `references/takes.md` under the key that `chosen_object` returns as `take`.
- A line `[[ only when: name ]]` opens a part that applies only when the answer has a value called `name`, and `[[ only when: no name ]]` one that applies only when it has none. `[[ end ]]` closes the part. Leave out a part that does not apply. The same marks can stand inside a line.
- `cut_copy` in those marks is not a value from the connector. It is the user's decision from step 7.
- `{#}` is the next number of a list that is numbered once through, counted after the parts that do not apply are left out.
- The instructions were first written to be handed out one at a time. Where one names `sketch_brief`, `develop` or `finish_brief`, it means the sketch, the build and the finishing instruction in these files; where it says "this service", it means Seed Lab.

## Which model is building

This process was tested with Claude Opus as the building model. In the blind votes behind it Opus was picked over Sonnet under the same process (29 of 41 pairs): Sonnet takes the borrowed object too far, into loud colour and dense layouts. That is all the evidence there is, and it is about Sonnet. If you are Sonnet, Haiku or another model smaller than Opus, hold back: carry the object by structure and order first, and keep density restrained. If you are another model, nothing here tells you to hold back. Say which model you are when you report to the user.
