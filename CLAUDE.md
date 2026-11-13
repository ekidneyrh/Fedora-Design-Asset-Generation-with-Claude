# Brand Asset & Design Rules

Whenever I ask you to generate or edit visual assets, graphics, or banners, you must automatically follow these constraints:

## 1. Brand Guidelines

**Official Color Palette** — use these exact hex codes:
- **Dark Fedora Blue:** `#294172`
- **Fedora Blue:** `#3c6eb4`
- **Primary:** `#51a2da`
- **Freedom Purple:** `#a07cbc`
- **Friends Magenta:** `#db3279`
- **Features Orange:** `#e59728`
- **First Green:** `#79db32`

**Typography:**
- **Heading font:** Montserrat (import via Google Fonts in `<style>` tags)
- **Body font:** Open Sans (import via Google Fonts in `<style>` tags)

## 2. Global Mascot & Mesh Gradient Safeguard
To prevent browser rendering errors, apply this rule to ALL mascot SVGs in `./assets/branding-and-logos/fedora-mascots/` folder:
- **Do not link to mascots using `<image>` or `<img>` tags.** You must inline the actual SVG XML code directly into the final banner SVG.
- **Do not modify, rewrite, or simplify the internal vector tags of mascot files** (specifically `<meshGradient>`, `<meshRow>`, `<meshPatch>`, or complex filters) while inlining them.
- Copy the structural tags or groups (`<g>`) from the mascot file and embed them exactly as-is into the SVG.

## 3. Strict Contrast & Readability Rules
To prevent hard-to-read designs, you must ensure strong visual contrast between the background and foreground:
- **Never place dark text on dark backgrounds, or light text on light backgrounds.**
- If you design a dark gradient background (e.g., transitioning between Fedora Blue `#3c6eb4` and Dark Fedora Blue `#294172`), **you must use pure white (`#FFFFFF`) or a very light, high-contrast color for all text, headlines, and logos**.
- If the background is light (e.g., light gray or white), use our Dark Fedora Blue (`#294172`) for text.
- Always double-check that foreground text is mathematically readable against whatever background element or gradient it sits on top of.

## 3A. Typography & Text Treatment Rules
For professional, clean visual communication:
- **Use clean text with subtle drop shadows only** — never apply heavy outlines, strokes, or comic-book style borders to headline text.
- **Text should float above the background**, not compete with it. Use soft drop shadows (4px blur, 3px offset, 40% opacity) for depth.
- **Avoid visual clutter** — if text needs emphasis, use size, weight, or color, not additional decorative effects.

## 4. Composition & Layout Rules
To ensure balanced, professional designs:
- **Apply the rule of thirds** — position main headlines in the upper third of the canvas, not crammed against the top edge.
- **Provide generous breathing room** — leave at least 60-80px margin from canvas edges for all text elements.
- **Center decorative elements vertically when possible** — avoid pushing illustrations, mascots, or graphics to extreme edges unless intentionally creating asymmetry.
- **Balance the composition** — distribute visual weight evenly. If text is top-heavy, center supporting elements in the middle or lower portion.
- **Maintain clear visual hierarchy** — the most important element should be immediately obvious. Don't let multiple elements compete for attention at the same visual weight.

## 5. Social Media & Blog Banner Branding Rules
- **Automatic Branding Requirement:** If the graphic being generated is a social media image, promo banner, or blog header, **it must be branded with the official Fedora logo** from `./assets/fedora-logo/` directory.
- **Logo Selection:** Use `fedora_white-horizontal.svg` for dark backgrounds, or `fedora_dark-background.svg` for light/mixed backgrounds.
- **Integrity of the Logo:** You must keep the logo entirely intact. Read the SVG file and embed it exactly as-is. Do not alter its proportions, strip its internal geometry, recreate it, or warp it.
- **Subtle but Readable Placement:** Position the logo subtly (typically in the top-left or bottom-right corner) so it acts as an elegant brand mark. **Do not scale it down too small**—it must remain clearly recognizable and readable (keep its width at a minimum of `100px` to `150px` for standard banners).

## 6. Background Treatment
When creating graphics for a specific Fedora release:
- **Check for release-specific wallpapers** in `./assets/wallpapers/` first
- Position the wallpaper to show key visual elements while preserving clear space for text in the upper portion
- If no wallpaper exists, prompt me to add it to the `./assets/wallpapers/` folder.

## 7. Saving Outputs
- Unless otherwise specified, always save newly generated compositions, banners, or graphics to the `./outputs/` directory.
- Create the `./outputs/` directory automatically if it does not exist. Do not overwrite original assets.
