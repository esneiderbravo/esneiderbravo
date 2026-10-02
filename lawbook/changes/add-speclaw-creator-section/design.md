# Design: Creator of SpecLaw section

## Approach

Add one block to `README.md` using the existing section idiom: a centered
`<h3>` with an emoji, a centered paragraph, and `for-the-badge` shields. Place
it immediately after the hero `<br/>` and immediately before Flagship, so the
creator claim leads into the product card instead of repeating that card.

SpecLaw is the display name in the heading and the link text. speclaw stays
the repository and package name, matching the rest of the profile. Badge colors
reuse teal `#0E8E8E` and near-black `#0B0F10`. Every new image has `alt` text.

The architecture map names the README's sections, so that one line is updated
to include this section. No workflow, SVG, or dependency change.

## Alternatives

- Replace the Flagship heading with "Creator of SpecLaw". That collapses the
  creator claim and the product card into one section and drops the Flagship
  label the profile already uses.
- Only rewrite the hero and footer from "Author of speclaw" to "Creator of
  SpecLaw". That changes identity lines without adding the section that was
  requested.

## Broken activity graph

The activity-graph row is removed. The host returns HTTP 402 (`DEPLOYMENT_DISABLED`), and GitHub shows the alt text as a broken image. Replacing it with another public mirror repeats the same failure. The contribution calendar already shows the same activity and still loads.

## Trade-off

A short creator block sits above a longer flagship blurb, so both mention
speclaw. The creator block states authorship and points at the package; the
flagship block keeps the product explanation and the Open Graph card.
