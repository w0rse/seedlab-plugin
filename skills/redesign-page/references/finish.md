# The finishing instruction

The instruction for finishing a page that has been built, as a template. Call the Seed Lab connector's `chosen_object` tool with the id the page was built from, fill the template with the values it returns as `SKILL.md` says under "Reading the reference files", and follow the result.

## Template

Finish the page built from `{id}`. The page exists in the project now; this is the last stage, and it is not a redesign.
First take screenshots of the page as it renders, at 1440 wide, one screen per picture from the top, up to six. Look at them before you read any code: "its screens are attached" in the instruction below means these.
Answer the numbered items and finish the page from this instruction. Then take new screenshots, send those to `review`, and act on the director's notes; repeat with fresh screenshots, up to three rounds in all.

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

The direction it was built to: {object_capitalised}.[[ only when: tradition ]] It is designed inside one tradition of graphic design: {tradition}. The tradition decides how it is composed and set; the object still decides what its parts are, and the colours are the ones set for this direction.[[ end ]][[ only when: take_title ]] How the object is applied on this page: {take_title}. {take_text}[[ end ]]

Its colours are set and stay: ground {ground}, second colour {second}, accent {accent}, text {ink}[[ only when: display_face ]], with {display_face} for the largest headings and {text_face} for everything else[[ end ]]. If they are not yet defined once as custom properties, make them so while you finish. To change them call `colours`; do not adjust them by eye.

[[ only when: working_part ]]
The working part ({working_part}) has to work now exactly as it did before the redesign. Try every control it has before you call the page finished.
[[ end ]]

## The project comes first
You are editing a real project, not starting one.
1. Before any design decision, read how the project is built: its framework, how it styles things, its components, its design tokens, the fonts it already loads, and how this page is routed and fed its content.
2. Build with what is there. Do not add a framework, a CSS library or a component kit, and do not change how the project is styled. A few custom properties and inline SVG are fine where the project has a place for them. Load no typeface the project does not already load, unless this instruction sets one.
3. Change this page only. Shared components, global styles and other pages stay as they are unless the user says otherwise; where this page needs a part to look different, make a version local to the page.
4. Use the project's real content. Do not invent facts, figures, customers, quotes or features, and do not leave placeholder text.
5. Everything that works must still work when you are done: links, forms, data, states, keyboard use, the widths the project supports, and the project's own checks. Where this instruction asks for something the project rules out, such as a phone width on a page with a fixed minimum width, the project stands and you say so.

## The finishing instruction
The direction below was written for a studio brief. Read it for a real project: "the content pack" is the content this page already has or the user has given you; "the acceptance criteria" are what the user asked for, plus everything on the page that already works and must keep working; "the creative director" is this service; "this client" and "this product" are the user's.

This is the art direction for this job, set by the creative director. These are requirements, not suggestions. Where the direction conflicts with what you would normally do, the direction wins. Where it conflicts with an acceptance criterion, the criterion wins.

This project already holds a finished page for this brief; its screens are attached, from the top. It was chosen over other attempts because its direction is right. Nobody would put it live as it is. Your job is to finish it, not to redesign it and not to tone it down. Before you change anything, find the one or two boldest things on the page: what a visitor would remember tomorrow. A bold thing is a field of colour, a scale, a structure, a headline, the way the main figure is drawn. Those stay, at full size and full strength: you may fix how they sit and what surrounds them, and you may not shrink, mute, simplify or remove them. Costume is not a bold thing and gets no such protection: lettering that imitates something, used below the largest headings; a cartoon or prop of the thing the page borrows from; a list or a table re-laid so that it is harder to read in order. A large figure is bold only if it shows something from this page's content. A drawing of the thing the page borrows from, or a diagram with invented data, is costume however big it is: redraw it from the page's own numbers, items or steps at the same size and strength, and only if the content has nothing to draw give its place to the headline. Where the page has those, keep the idea and bring the part back to something a reader can use: plain text in reading order, the idea held by structure, type and colour. Then bring the execution to the standard of a page a good studio ships under its own name: spacing with a rhythm, one type scale, things that align, no stretch that is crowded or empty, and the same care in the lower sections as on the first screen. Remove small things nobody would miss: labels, captions, numbering and explanations the content did not supply. The words stay as they are on the page: where the copy was cut or shortened that was deliberate, so do not restore it, and add no words of your own. Make narrow widths, hover and focus right. Do not start again, and do not swap the idea for another.

{#}. **idea**: The page's idea as you found it, in one sentence.
{#}. **bold**: The one or two boldest things on the page, each named exactly. These stay at full size and strength.
{#}. **costume**: Any costume on the page: imitation lettering below the largest headings, a cartoon or prop, a reading section that is hard to read in order. Say what each becomes. If there is none, say so.
{#}. **defects**: What else stops this page from going live as it is, most important first: at least four things, each naming where on the page.
{#}. **removed**: The small things you will take out, and why nobody would miss them.

Before you change anything, answer each numbered item above in your reply to the user, in a line or two, using its bold word as the label. Then finish the page.
