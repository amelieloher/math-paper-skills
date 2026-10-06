# Figures

Figures are where a visual paper earns its name, and where it can most easily say
something false. Treat a figure as a set of claims. Whether a figure or animation
should exist at all, and how to design, draw and review it, is governed by the
[`math-figures`](../../math-figures/SKILL.md) skill: a visual is made only when it
expresses or teaches a mathematical idea. This reference adds what is specific to a
website.

## Pipeline

1. **Proposals.** Section writers list one-line figure ideas while writing nodes.
2. **Design.** A writer, acting as figure designer, writes a spec per figure: what it shows,
   each visual element as a claim citing the source spans, whether it is
   `schematic` or `quantitative`, the parameters of any simulated or toy run (labelled
   as such on the page), the colour roles, and the interaction (sliders, toggles).
3. **Spec audit** as claims, then ★ the authors approve the list.
4. **Build.** A builder implements each approved spec as a D3 module (interactive) or
   TikZ → SVG (static), using theme tokens only.
5. **Build check.** A different auditor compares screenshots and the running figure
   with the spec, including the design pseudo-claim (the spec's visual promises).
   Several rounds are normal; record contradicting verdicts honestly.
6. **Approval.** The figure's status goes from `review` to `approved` only on the
   authors' word; the site shows an "awaiting author review" badge until then. Make
   the badge key on the schema's final status value (a mismatch once badged every
   approved figure).

## Implementation rules

- **Real mathematics in figures.** Render labels and captions with KaTeX, inside SVG through
  `foreignObject`, with the paper's macro table, and a plain-text fallback for
  snapshot renderers. Check every figure for raw TeX (e.g. a macro name shown as
  text) and KaTeX errors in a headless browser.
- **WebKit (Safari, every iOS browser) mispositions and misscales HTML inside
  `foreignObject`** under group transforms and viewBox scaling: the KaTeX labels pile
  up at the figure's top-left while Chromium and Firefox look fine. In WebKit keep the
  `foreignObject` as an empty placeholder and draw the label in an HTML layer over the
  SVG: map the placeholder into the SVG's user space with
  `svg.getScreenCTM()⁻¹ · fo.getScreenCTM()` (ancestor CSS transforms cancel), then to
  CSS pixels with the untransformed viewBox scale and the SVG's offset in its
  container; re-sync on resize. Test every figure in Playwright's WebKit
  (`npx playwright install --with-deps webkit`).
- **Pop-out.** Small figures need a click-to-enlarge dialogue in which the sliders keep
  working; re-lay out on resize rather than scaling pixels, except for a final uniform
  scale-to-fit: the enlarged figure must fit one screen, so lay it out at full width
  and, if it is taller than the dialogue, scale the whole figure (controls included)
  down to the dialogue's height. Measure widths with `offsetWidth`, never
  `getBoundingClientRect`, which includes that scale and feeds back into the layout
  until the figure is unreadably small. A tall single-column module needs a wide
  layout to fit at a readable size.
- **Resizing.** Figures must follow their container's width (after divider moves,
  text-size changes, pop-out) via a resize observer, without re-running setup.
- **Theme.** Colours come from CSS tokens with light and dark values; a missing token
  renders black. Check both themes.
- **Captions.** Show the title and one or two lead claims; put the rest under a closed
  "Full explanation". Every claim stays in the page (the publish check needs it).
- **Illustration facts are not claims.** Label illustrations "numerical illustration"
  or "illustrative path". Facts about the illustration itself (simulated, sample size,
  seed, parameters, a numerical check, an illustrative value of a constant) go in the
  figure's illustration parameters,
  shown under "about the illustrative data", never in a caption claim: no paper span
  can support them, and auditors reject them.
- **Simulated figures.** A static picture of a pre-computed simulation labelled as an
  illustration makes readers look for a run button. Offer the authors runnable
  versions: an in-browser simulator of the same model with a seeded generator,
  "New sample" showing the seed, "Play" where the motion matters, and a deterministic
  render in snapshot mode for the audit images.
- **Findability.** A figure shows only on the node it attaches to, and readers could
  not find several. Add a "Figures" menu in the top bar (thumbnail, title, location;
  a click opens the node and scrolls to the card), a figure marker on graph nodes
  with per-section counts, a "Figures in this section" list on section pages, and
  make sure setting nodes that carry figures are readable, not faded.
- **Bundling for a preview.** If figures are bundled into one file, resolve sibling
  imports by their full relative path (`lib/dom`, not `dom`). A bug here once shipped
  a preview with no figures at all, undetected because only the bundle text was
  compared. Only a real browser run catches this.

## Animations

Design and production follow `math-figures`' [animations](../../math-figures/references/animations.md).
On the website, chapter titles and summaries shown as text are claims, cited and
audited like captions, and the design brief is audited too. The card: a clickable
chapter list, a few playback speeds, a poster, Enlarge that fits one screen, no
autoplay, and a way to give the player generous width.
