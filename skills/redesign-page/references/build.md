# The build instruction

The instruction for rebuilding the page in the direction the user chose, as a template. Call the Seed Lab connector's `chosen_object` tool with the id, fill the template with the values it returns as `SKILL.md` says under "Reading the reference files", and follow the result. `cut_copy` is the user's decision on whether the page's copy may be cut.

The numbered part of it, from "This is the art direction for this job" to the line that asks for one decision for each numbered item, is the text pages were built from and voted on. The rest is Seed Lab's own wording for working in a real project, and has not been through a vote.

## Template

# `{id}`: {object}

**The problem to solve.** {problem}
**What people come to this page to do.** {purpose}
[[ only when: keep ]]
**What must keep working.** {keep}
[[ end ]]
[[ only when: working_part ]]
**The working part of the page.** {working_part}
[[ end ]]
**Product.** {product}
**Audience.** {audience}
**Page.** {page_type}

{description}

## The project comes first
You are editing a real project, not starting one.
1. Before any design decision, read how the project is built: its framework, how it styles things, its components, its design tokens, the fonts it already loads, and how this page is routed and fed its content.
2. Build with what is there. Do not add a framework, a CSS library or a component kit, and do not change how the project is styled. A few custom properties and inline SVG are fine where the project has a place for them. Load no typeface the project does not already load, unless this instruction sets one.
3. Change this page only. Shared components, global styles and other pages stay as they are unless the user says otherwise; where this page needs a part to look different, make a version local to the page.
4. Use the project's real content. Do not invent facts, figures, customers, quotes or features, and do not leave placeholder text.
5. Everything that works must still work when you are done: links, forms, data, states, keyboard use, the widths the project supports, and the project's own checks. Where this instruction asks for something the project rules out, such as a phone width on a page with a fixed minimum width, the project stands and you say so.

## A redesign, to solve the problem
This is a redesign and not a repaint. If the page exists already, its present layout is not kept: its order, its grouping and its components are all open, and new colours and type on the layout it has now would not answer the problem. What is kept is the page's content, what people come here to do, and everything listed as having to keep working. Before the numbered decisions, tell the user in two or three sentences how the page organised by this object solves the problem above better than the page as it stands.

[[ only when: working_part ]]
## The working part
The main content of this page is a working thing: {working_part}. It is content, not a component to be restyled away. It stays, and it stays working: every control, state, link and value it has now. Under the rule about figures in the direction below, it is the large figure that shows something true from the page's content, so it can take the size and the place the object gives its main part. The object decides how the page is organised around it: how it is framed, keyed, ordered and labelled, and what sits beside it. The object does not replace it with a picture of itself, does not redraw it as something it is not, and puts no decoration over it. Where the object's form and the working thing's use disagree, use wins. If the page has several working things, the one people come for takes the main place, and the others keep working where the object puts them.
[[ end ]]

## The direction
The direction below was written for a studio brief. Read it for a real project: "the content pack" is the content this page already has or the user has given you; "the acceptance criteria" are what the user asked for, plus everything on the page that already works and must keep working; "the creative director" is this service; "this client" and "this product" are the user's.

This is the art direction for this job, set by the creative director. These are requirements, not suggestions. Where the direction conflicts with what you would normally do, the direction wins. Where it conflicts with an acceptance criterion, the criterion wins.

Before anything else, decide how much design this page can carry. Some pages are worked from, not looked at: a page of reference, a settings screen, a form, a table of records. A good designer gives those almost nothing: exact type, a clear order, one or two decisions, and no ornament or imagery at all. Other pages are there to be noticed and can carry a great deal. Sometimes the best design is very nearly none. Place this page on a scale from 1 (worked from) to 5 (made to be noticed), and apply the rest of this direction at that strength. At 1 or 2, take from the direction only what makes the page easier to use, such as its way of ordering and numbering things, and leave out its imagery, its ornament and its mannerisms.

When `directions` was called this page was placed at {register}. {register_why} Judge it again now from its real content.

{#}. **register**: Where this page sits from 1 (worked from) to 5 (made to be noticed), as a single number, and why.
{#}. **strength**: What you will take from the rest of the direction at that strength, and what you will leave out.

[[ only when: cut_copy ]]
Cut the copy to half. The content pack is about twice as long as this page should be, and permission to cut it is not enough: builders given that permission keep nearly every word. Count the words in the content pack, and put at most half that many on the page, counting everything a visitor can read. Decide what the page is for, keep what serves that, and drop the rest: whole sections, repeated points, anything said twice in different words, anything a visitor would not miss. Shorten what stays. Add nothing of your own. The facts the acceptance criteria name have to survive.

{#}. **word_budget**: The number of words in the content pack, and the number of words on your page.
{#}. **cut**: What you cut, and the one thing you were least sure about cutting.

[[ end ]]
This page is built out of an object from outside web design: {object}. It was chosen for this client from three candidates, by its job, its readers and its way of ordering things, and not because it pictures the subject. The page's organisation is the object's, and so are its parts: every block of content is built as a part that object really has, in the form that part takes there, and not as a web component dressed up. If the object has no card, no banner and no column of equal boxes, neither does this page. The object is carried by structure, order, scale, type and colour. It is not carried by costume: no imitation paper, no props, no cartoon of the object, and lettering that imitates the object only in the largest headings. Whatever the object, the parts of the page that people read at length or look things up in, such as running text, a list of points and a table, stay plain, in reading order and easy to read. A large figure is welcome when it shows something true from this page's content: its numbers, its items, its steps, at any size. A picture of the object itself, or a diagram filled with made-up data, shows the visitor nothing and is not wanted. It must still work as a web page for this product.

{#}. **object**: The object: {object}.
{#}. **parts**: For each block of content on this page, name the part of that object it is built as.
{#}. **mapping**: State how the whole page is organised the way that object is, from the first screen to the last section.
{#}. **plain**: Name the parts of this page that people read at length or look things up in, which stay plain.

[[ only when: tradition ]]
Design this page inside one tradition of graphic design. Work from its actual rules of composition, typography and colour, applied to this product, not from its surface clichés. Where the tradition's colours and the set colours disagree, the set colours stand.

{#}. **tradition**: {tradition}.

[[ end ]]
[[ only when: take_title ]]
How the object is applied on this page: {take_title}. {take_text}

[[ end ]]
This page adds no words of its own. Pages like this one are usually given away by text added to everything: a small label over every heading, a caption under every figure, numbers on the sections, tags, badges and one-line explanations of what is already plain. Leave all of that out.

{#}. **no_added_words**: Every word on the page is either in the content pack or a label without which something could not be used. No eyebrows, captions, section numbers, annotations, taglines, tags or explanatory lines of your own.
{#}. **say_it_once**: Each thing is said once. Where a heading says it, no line under the heading says it again.
{#}. **clear_without_labels**: Where you would add a label to make something clear, change the design until it is clear without one. Say where you did this.

[[ only when: no display_face ]]
The colours of this page are set. They were built the way a colourist builds a palette, from a ground colour and its relations on the colour wheel, and each has a share of the page. Use these exact values in about these proportions. The ground is a field of colour that covers the page, not a tint behind white boxes; the second colour takes whole areas; the accent is rare and goes only where the eye should land. Any further shade is one of these made lighter or darker. No other hue, no gradient from one hue to another, and no pure white or pure black unless one of these is.

{#}. **ground**: Ground, about 60% of what is on screen: {ground}
{#}. **second**: Second colour, about 30%: {second}
{#}. **accent**: Accent, about 10%, never for running text: {accent}
{#}. **ink**: Text on the ground: {ink}
{#}. **scheme**: How they relate: {relation}. Say where each colour goes on this page.

[[ end ]]
[[ only when: display_face ]]
The colours and typefaces of this page are set. The colours were built the way a colourist builds a palette, from a ground colour and its relations on the colour wheel, and each has a share of the page. Use these exact values in about these proportions. The ground is a field of colour that covers the page, not a tint behind white boxes; the second colour takes whole areas; the accent is rare and goes only where the eye should land. Any further shade is one of these made lighter or darker. No other hue, no gradient from one hue to another, and no pure white or pure black unless one of these is. Two typefaces and no third: the display face only in the largest headings, set large with tight spacing, and the text face for everything else in at most two weights. One scale of five sizes for the whole page.

{#}. **ground**: Ground, about 60% of what is on screen: {ground}
{#}. **second**: Second colour, about 30%: {second}
{#}. **accent**: Accent, about 10%, never for running text: {accent}
{#}. **ink**: Text on the ground: {ink}
{#}. **scheme**: How they relate: {relation}. Say where each colour goes on this page.
{#}. **display_face**: Display typeface, for the largest headings only: {display_face} (Google Fonts)
{#}. **text_face**: Text typeface, for everything else: {text_face} (Google Fonts)

[[ end ]]
Before you edit a file, write one concrete decision for each numbered item above in your reply to the user, using its bold word as the label. Then build.

## The colours, defined once
Define the four colours once, as custom properties on this page's outermost element (`--page-ground`, `--page-second`, `--page-accent`, `--page-ink`), or as this page's own values for the project's colour tokens where it has them. Everywhere else refer to them, and write no colour value a second time. A lighter or darker shade is mixed from one of the four, for example `color-mix(in oklch, var(--page-ground) 85%, var(--page-ink))`, and is not written as a value of its own. The palette can then be changed after the page is built by changing four values, which `colours` gives. Text set on the second colour is the text colour or the ground, whichever reads better there, mixed towards the other until it reaches 4.5:1.

Colour that carries meaning is content, not palette: the scale that colours a map or a chart by a value, and status colours such as late, blocked and done. Do not drop what such colour says. Where the four colours and their shades can carry the same distinctions, rebuild it from them and say how each distinction is now shown; where they cannot, as with a data scale of many steps, keep that scale as it is and let the set colours govern everything around it.

[[ only when: no cut_copy ]]
The copy is not to be cut. Every word the page has now stays, in the user's wording, unless the user says otherwise; shorten nothing on your own.
[[ end ]]

This process was tested with Claude Opus building. Sonnet, under the same instruction, took the object too far, into loud colour and dense layouts, and was picked less often in the blind votes behind it. That finding is about Sonnet, and is taken to hold for Haiku and other models smaller than Opus: for them, structure and order first, density held back. Nothing was measured for other models.

What in this instruction was tested: the numbered direction is the text pages were built from and voted on. The project rules, the paragraph on redesign, the paragraph on the working part and the rules to define the colours once and to keep colour that carries meaning are this service's own wording and have not been through a vote.

When the whole page renders, call `finish_brief` with this id.
