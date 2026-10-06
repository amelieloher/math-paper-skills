# The site and its launch

## What the reader gets

- **Welcome panel**: title, authors, what the site is, how to read the graph, what is
  checked and how (state it precisely, including any author waiver), what the Lean
  check means, and buttons to start at the main theorem. When the paper is on arXiv:
  the arXiv link and a "How to cite" line. A footer with ©, the Lean repository and
  third-party licences (and `THIRD_PARTY_LICENSES.txt` in the build). Do not grant a
  licence for the paper content unless the authors decide one.
- **Graph views** (Cytoscape + dagre):
  - *whole map*: sections and theorems closed; click a section to open it in place;
  - *cluster view*: an opened section or subsection with only its direct outside
    links as context, so edges stay short;
  - *focus view* of a result: what it uses on the left, what uses it on the right,
    one or two hops. Readers get lost in one big zoomed-out graph; these local views
    are what made navigation work.
  - Legend, including "A → B: A is used in the proof of B"; zoom buttons; "fit the
    view" with an icon that does not look like full screen; a real "expand graph to
    full width" button (Esc returns).
- **Reading panel**: summary, exact statement, uses / used by, Lean badge, figures,
  proof idea, numbered steps each with a one-line summary and the paper's own text.
  Every notation symbol opens its definition card.
- **Reading mode**: a draggable divider (keyboard accessible), "Hide graph" (`g`), and
  a text-size control scaling only the panel (line length kept in `ch`). Remember
  settings in `localStorage` behind try/catch.
- Search, deep links `#/<id>/<level>`, light and dark themes, and a phone layout with
  Graph / Reading tabs and an outline list instead of the canvas.
- **Back and Forward.** Ask the authors what Back means. Plain browser history
  replays every zoom and view change. Authors may prefer "up the proof chain": Back
  goes to a result that uses the open one (to the one the reader came from, or a
  chooser when several qualify; disabled at a main theorem), Forward retraces, and
  view changes are not steps.
- **External-source toggle.** A "show companion links" switch must visibly change
  every view. In the main-results view, include the external results reached through
  hidden supporting steps, not only direct uses, which can hide most of them. In the
  full graph, give the external
  region the weight and colour of a section.
- **PDF downloads.** Publish each PDF under a stable, chosen file name. Authors put
  these URLs in their papers (a companion manuscript cited by URL), so a rename
  breaks citations; coordinate it. Empty the output `pdf/` directory on every build,
  or the old copy lingers. The LaTeX-to-HTML converter must handle the bibliography's
  `\url` and `\href`, and the preview's host allowlist must include the site's own
  host.

## Layout pitfalls

- **Scrollbar feedback loop.** At fractional browser zoom a whole-pixel canvas can
  overflow its pane by a pixel; the page's scrollbars appear, the graph shrinks and
  re-fits, the scrollbars vanish — the page shakes at about 10 Hz. Make the desktop
  layout an app shell (`html, body { overflow: hidden }`, only panes scroll) and
  ignore sub-pixel resize events. Headless Chromium hides scrollbars by default; test
  with them shown and with page zoom 0.8–1.5.
- Re-fit the graph after every pane size change (divider, hide/show, expand), but
  never in a loop.
- Serve under a sub-path (GitHub project pages live at `/<repo>/`): relative asset
  URLs only; test deep links, figures, popovers and fonts under the sub-path.
- Declare UTF-8 (`<meta charset="utf-8">`) and serve with a charset.

## Privacy and publishing

- The source repository (content, audit trail, briefs, reports, canary material)
  stays **private**. Never enable Pages on it: Pages on a private repository can be
  public.
- Publish only the built `dist/` to a separate public repository (e.g.
  `<owner>/<name>-paper`, served by GitHub Pages), with `.nojekyll`.
- Before the first deploy, grep the build for private material: home paths, auditor
  and ledger details, canary text, internal repository names.
- The public repository may belong to an author: the author creates it empty, invites
  the deploying account with write access, and enables Pages (it needs admin rights).
  Set the canonical URL before the first deploy.
- If a public error must be fixed while the main branch cannot pass its checks (for
  example, unaudited new content), deploy from the last good commit plus only the
  fix. The deploy commit must cite real commits.
- Once the site is public, a size budget that existed only for a private preview host
  may be relaxed; log the change in the plan of record.
- Deploy from a dedicated clone of the private repository (never someone's working
  tree): require a clean tree; install if needed; extract, build, run all checks;
  rsync `dist/` into the public clone with `--delete --exclude .git`; commit
  "Deploy site built from private commit <sha>"; push.
- Head metadata: title, description, canonical URL, Open Graph and Twitter tags, an
  Open Graph image rendered from the site's own colours (resvg), an SVG favicon with
  PNG fallback.
- While the site is private, preview it through a private host. Smoke-test every
  preview in a headless browser before publishing it.

## Launching with an arXiv posting

Authors often want the site and the Lean repository live before the arXiv posting so
that the arXiv comments can link to them.

- Keep `arxiv_id: null` in `site.yaml`; the arXiv link and citation line appear only
  when it is set, and a test builds with a fixture id.
- Install a watcher (a plain cron entry every 30 minutes, silent before a start time)
  that queries the arXiv API with one `ti:` term per title word and the first
  author's surname — a quoted `ti:"…"` phrase fails once short words are dropped —
  and accepts a result only on normalised title equality and all author surnames.
  On a match it sets `arxiv_id`, commits, redeploys, pushes and removes its own cron
  line. Log to a private file.
- Test the watcher end to end before installing it: dry run on an already-posted
  paper, then a full run against local bare-repository remotes.
