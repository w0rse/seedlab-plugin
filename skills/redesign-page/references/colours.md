# Colours

Every direction comes with a palette of four colours, built by colour-wheel rules: a ground, a second colour, an accent and a text colour. The Seed Lab connector's `colours` tool works on one direction and changes nothing else about it: its objects, its takes and its ids stay the same.

- With the id alone, it returns the colours as they stand.
- `redraw: true` gives the direction another palette. `palette` with an earlier number goes back to that one; 1 is the palette the direction came with.
- `contrast` and `colour` run from -1 to 1, and 0 is the palette as drawn. `contrast` moves the ground away from the text and the second colour away from the ground. `colour` is how much colour the ground and the second colour carry; -1 is close to grey. Hues and the scheme do not change.
- `typefaces` sets, or stops setting, two typefaces from Google Fonts for the direction.
- `clean` chooses the rules a palette is drawn by. True, the default, keeps most grounds light and leaves out dull warm colours. False is the first rules, the ones the vote on colours was held on. The cleaner rules have not been voted on yet.

The server remembers the setting, and `chosen_object` returns the colours as last set.

## Whose choice it is

In the blind vote more contrast was picked in 11 of 41 pairs, and mostly on mid-toned grounds. So 0 is the default and the choice is the user's: offer it, do not decide it.

## When a call changed the colours

The answer has `changed: true`, the four values as they are under `colours`, and the four as they were under `was`. If nothing is built yet, there is nothing to do: the next `chosen_object` gives the new colours.

If a sketch or the page is already built, change the four values where they are defined, and nothing else:

| | custom property | value in the answer |
|---|---|---|
| ground | `--page-ground` | `ground` |
| second colour | `--page-second` | `second` |
| accent | `--page-accent` | `accent` |
| text | `--page-ink` | `text` |

If a value was written in more than one place, replace every occurrence, and do all four in one pass through placeholders, so that one colour's new value is never taken for another's old one. Shades mixed from the four follow by themselves; a shade written as a value of its own is made again from the new colour by the same step. Then look at the page at 1440 wide and at the narrowest width the project supports. `text_on_ground_contrast` and `accent_on_ground_contrast` in the answer are the contrast of the text and of the accent on the ground.
