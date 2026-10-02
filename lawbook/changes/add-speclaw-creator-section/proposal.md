# Proposal: Add the Creator of SpecLaw section

## Why

The profile already showcases speclaw as the flagship project and calls Esneider
its author in the hero and footer. It does not state, as its own section, that
he created SpecLaw — the name visitors should associate with that work.

## What

Add a centered profile section titled **Creator of SpecLaw**, placed after the
hero and before Flagship. The section links SpecLaw to the speclaw repository,
names the published tool **speclaw**, and shows brand-matched badges for GitHub
stars, the npm package, and the license. Existing sections stay in place.

The public activity-graph host (`github-readme-activity-graph.vercel.app`) is disabled (HTTP 402, `DEPLOYMENT_DISABLED`) and renders as a broken image on the profile. Remove that image. The contribution calendar stays.

## Non-goals

- Renaming the npm package, the repository, or the hero/footer "Author of speclaw" lines.
- Changing the metrics workflow or generated SVGs.
- Publishing to `main` (the live profile) without an explicit push.

## Migrations

None.
