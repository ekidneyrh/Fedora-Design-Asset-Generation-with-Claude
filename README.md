# Fedora Design Asset Generation with Claude

A template project directory for generating brand-compliant **SVG** design assets for the Fedora Project using the [Claude Code CLI](https://code.claude.com/docs/en/quickstart).

This repository is the companion to the blog post **[Fedora Design Asset Generation with Claude](TODO-ADD-BLOG-POST-URL)**, which explains the reasoning behind the workflow and walks through a real case study (the Fedora Linux 45 Release Party assets).

> **This is a template, not an asset library.** The `assets/` directory is empty by design — the real Fedora design assets live on the Fedora forge and run to over a gigabyte. See [`assets/README.md`](assets/README.md) for where to get them and how to lay them out.

---

## Why this exists

The Fedora Design Team works in three-week sprint cycles, which means incoming tickets are only reviewed every three weeks. That works well for planned work, but creates friction for genuine last-minute requests — which usually end in either a declined ticket or a disrupted sprint.

This workflow treats urgent, low-complexity requests as a **separate service**, optimised for speed rather than deep iteration.

The key requirement was **SVG output**. As an open source team, everything we produce needs to be an editable source file that anyone can pick up and change later. SVGs also convert cleanly to CMYK for print, and they mean a designer can take a generated file and finish it by hand in Inkscape rather than starting from scratch.

## How it works

Claude Code writes raw SVG XML. It sets up the background using the official brand colours, imports Montserrat and Open Sans via Google Fonts, positions the text and accent elements, and inlines mascot and logo vector data directly into the file. Because the output is code rather than a raster image, the result is a real, editable source file.

The three pieces of the directory do the following:

| Path | Purpose |
| --- | --- |
| [`CLAUDE.md`](CLAUDE.md) | The rulebook. Claude reads this automatically on every request. |
| [`assets/`](assets/README.md) | Local copy of the Fedora design assets Claude draws from. Not committed. |
| [`outputs/`](outputs/README.md) | Where generated files are saved. |

## Repository structure

```
claude-fedora-design/
├── CLAUDE.md          # Brand rules Claude reads on every request
├── assets/            # Source assets — empty here, see assets/README.md
└── outputs/           # Generated SVGs and PNG previews
```

That's the whole thing. Three items at the top level, and only one of them is a file you write.

## Quick start

1. **Install the Claude Code CLI** — follow the [quickstart guide](https://code.claude.com/docs/en/quickstart).

2. **Clone this template:**

   ```bash
   git clone https://github.com/ekidneyrh/Fedora-Design-Asset-Generation-with-Claude.git claude-fedora-design
   cd claude-fedora-design
   ```

3. **Populate `assets/`** with the Fedora design assets — see [`assets/README.md`](assets/README.md).

4. **Adapt `CLAUDE.md`** to your own brand if you aren't working on Fedora. The structure transfers to any brand; only the values change.

5. **Run Claude and prompt it.** The initial prompt doesn't need to be detailed, because the brand guidelines and assets are already in context:

   ```
   Create an Instagram post promoting the nominee interviews for the F46
   Fedora Mindshare elections. Include a mascot that fits best.
   ```

6. **Iterate**, either by prompting Claude again or by opening the SVG in Inkscape and finishing it by hand.

## The CLAUDE.md file

`CLAUDE.md` is the heart of this setup. It acts as a standing set of instructions that Claude reads before every request, so you don't have to restate your brand rules each time. The version in this repo covers:

- **Colour palette** — the official Fedora hex codes
- **Typography** — Montserrat for headings, Open Sans for body
- **Mascot and logo handling** — inline the SVG XML, never link or redraw it
- **Contrast rules** — never light text on light backgrounds, or dark on dark
- **Composition rules** — rule of thirds, minimum margins, visual hierarchy
- **Automatic branding** — social graphics always get the Fedora logo
- **File management** — everything saves to `./outputs/`

Most of these rules started as a correction. When something came out wrong, I asked Claude to add a rule preventing it, and it edited the file itself. Expect yours to grow the same way — treat it as a living document rather than something you write once up front.

## Example outputs

Two finished examples generated with this setup are included in [`outputs/`](outputs/):

| Preview | File |
| --- | --- |
| ![F45 Release Party Mastodon graphic](outputs/fedora-45-release-party-mastodon.png) | [`fedora-45-release-party-mastodon.svg`](outputs/fedora-45-release-party-mastodon.svg) |
| ![F45 Mindshare nominee interviews Instagram post](outputs/f45-mindshare-nominee-interviews-instagram.png) | [`f45-mindshare-nominee-interviews-instagram.svg`](outputs/f45-mindshare-nominee-interviews-instagram.svg) |

Both are self-contained SVGs with the mascot, logo and wallpaper vector data inlined — open them in Inkscape to inspect or edit.

## Things worth knowing

- **Generation is not instant.** Writing an SVG by hand takes Claude a few minutes per asset — roughly 4 minutes in the examples above.
- **Large source files eat context.** The F45 wallpaper SVG is a big, complex file, and inlining it noticeably increases token usage.
- **Everything still gets a human review.** This workflow is for routine, fast-turnaround graphics. It doesn't replace high-touch design iteration on major initiatives, and output should be checked against the brand guidelines before publishing.
- **Claude Code is a paid service.** I have access through work. The [Claude web UI](https://claude.ai) has a free tier, though it's more limited for this kind of task.

## Fedora Design Team

- **Request a design:** [open a ticket](https://forge.fedoraproject.org/design/tickets/issues/new/choose)
- **Chat:** [#design:fedoraproject.org](https://matrix.to/#/#design:fedoraproject.org) on [chat.fedoraproject.org](https://chat.fedoraproject.org/)
- **Brand guidelines:** [docs.fedoraproject.org/en-US/project/brand](https://docs.fedoraproject.org/en-US/project/brand/)

## License

<!-- TODO: choose a license for this repo. The structure/docs are your own work;
     the example outputs in outputs/ are Fedora design assets and are governed by
     the Fedora brand guidelines linked above. -->

The templates and documentation in this repository are provided as-is. The example outputs in `outputs/` are Fedora Project design assets and are subject to the [Fedora brand guidelines](https://docs.fedoraproject.org/en-US/project/brand/).
