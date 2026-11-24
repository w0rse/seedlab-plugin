# The sketch instruction

The instruction for building the first screen of one chosen object or take, as a template. Call the Seed Lab connector's `chosen_object` tool with the id, fill the template with the values it returns as `SKILL.md` says under "Reading the reference files", and follow the result.

## Template

Build a sketch of the first screen only, for `{id}`. It is one of several the user will compare side by side, so it has to show the idea plainly, and it does not have to be finished.

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

**The object.** {object_capitalised}. {kind_orders}
**On this page.** {on_this_page_capitalised}.
[[ only when: tradition ]]
**The tradition.** It is designed inside one tradition of graphic design: {tradition}. The tradition decides how it is composed and set; the object still decides what its parts are, and the colours are the ones set for this direction.
[[ end ]]
[[ only when: take_title ]]
**This take: {take_title}.** {take_text}
[[ end ]]

**The colours.** [[ only when: no display_face ]]The colours of this page are set. They were built the way a colourist builds a palette, from a ground colour and its relations on the colour wheel, and each has a share of the page. Use these exact values in about these proportions. The ground is a field of colour that covers the page, not a tint behind white boxes; the second colour takes whole areas; the accent is rare and goes only where the eye should land. Any further shade is one of these made lighter or darker. No other hue, no gradient from one hue to another, and no pure white or pure black unless one of these is.
- Ground, about 60% of what is on screen: {ground}
- Second colour, about 30%: {second}
- Accent, about 10%, never for running text: {accent}
- Text on the ground: {ink}
- How they relate: {relation}. Say where each colour goes on this page.[[ end ]][[ only when: display_face ]]The colours and typefaces of this page are set. The colours were built the way a colourist builds a palette, from a ground colour and its relations on the colour wheel, and each has a share of the page. Use these exact values in about these proportions. The ground is a field of colour that covers the page, not a tint behind white boxes; the second colour takes whole areas; the accent is rare and goes only where the eye should land. Any further shade is one of these made lighter or darker. No other hue, no gradient from one hue to another, and no pure white or pure black unless one of these is. Two typefaces and no third: the display face only in the largest headings, set large with tight spacing, and the text face for everything else in at most two weights. One scale of five sizes for the whole page.
- Ground, about 60% of what is on screen: {ground}
- Second colour, about 30%: {second}
- Accent, about 10%, never for running text: {accent}
- Text on the ground: {ink}
- How they relate: {relation}. Say where each colour goes on this page.
- Display typeface, for the largest headings only: {display_face} (Google Fonts)
- Text typeface, for everything else: {text_face} (Google Fonts)[[ end ]]

[[ only when: working_part ]]
**The working part.** {working_part_capitalised} appears in the sketch as it really is: a screenshot of it taken from the page as it renders now, cropped and placed at the size and position this direction gives it, or its real markup with its real values; where the real component cannot run in a static file, a plain redraw from its real values will do. Do not draw a stand-in with made-up content, and do not invent figures, places or labels for it. It does not have to work in the sketch. What the sketch shows is how the page is organised around it: its frame, its key, its order and its labels.
[[ end ]]

**What to build.**
1. One screen at 1440 by 900 and nothing below it: no lower sections, no narrow widths, no hover states, no polish.
2. Put it where it cannot disturb the project: a single self-contained file such as `sketches/{id}.html` with its styles inline, or a throwaway route if the project cannot serve a static file. Do not touch the real page, shared components or global styles.
3. The sketch answers the problem above. It shows the page organised differently, not the layout it has now in new colours. Say in one sentence, before you build, what this object changes about how the page works for the people who come to it.
4. Use the page's real words and real figures: its actual headline, its actual first paragraph, its actual numbers. No placeholder text and no invented copy or data.
5. Every element on the screen is a part this object really has, in the form that part takes there. If the object has no card, no banner and no row of equal boxes, neither does the sketch. The object is carried by structure, order, scale, type and colour, and not by costume: no imitation paper, no props, no cartoon of the object. A large figure shows something true from this page's content; a picture of the object, or a diagram with made-up data, is not wanted.
6. Define the four colours once, as custom properties (`--page-ground`, `--page-second`, `--page-accent`, `--page-ink`), and refer to them everywhere, so that they can be swapped later.
7. Add no words of your own: no small label over the heading, no captions, no tags, no numbering the content did not have.
8. Anything a visitor would read at length stays plain and in reading order. On this page that is {plain}.
9. This page can carry about {register} on a scale from 1 (worked from) to 5 (made to be noticed). Sketch at that strength.
10. Decide quickly and commit: one idea carried through the whole screen is worth more than three half-carried.

**Then.** Take a screenshot of the sketch at 1440 by 900. When every direction has a sketch, show the screenshots to the user together, each under its id and its object, with the page as it is now beside them, and ask which to take further. Do not choose for them. For the one they prefer, call `variations` for further takes on the same object, or `develop` for the full instruction.
