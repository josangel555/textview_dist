# TextView — distribution bundles

Pre-built **release (production)** builds of TextView (MarkdownViewer), one zip per date.

**Source code:** the complete development history is published as a read-only archived
snapshot at **<https://github.com/josangel555/textview_archive>** (MIT) — every commit,
not maintained (no issues/PRs), but it builds into a runnable app with one command
(`bash scripts/build-app.sh release`; see its README). Product page:
<https://josangel.com/textview/>.

> **Use `TextView-2026-08-27.zip`** (latest): the panes-polish wave. The app
> starts ~10× faster (5.6s → 0.5s). Splits are fully session-contained and
> self-consistent: every close/move/cycle verb is pane-scoped (Close Other
> Tabs, Close to the Right, Move Tab Left/Right, ⌃Tab), only the active
> pane's tab wears the blue accent (the other pane's front goes grey),
> opening files in one pane can't blank or steal from the other, and closing
> a tab returns to the previously selected one (MRU). Also: the dead click
> band above the tab text is gone (invisible titlebar overhang), stuck drag
> "ghost chips" are impossible (liveness watchdog), the editor's horizontal
> scrollbar no longer jumps while typing, markdown previews auto-refresh on
> disk changes in every pane, markdown links are blue again, the CM6
> pointer no longer flickers, and closed sessions are recoverable for 30
> days via **Recently Closed ▸** (plus Save Session As… for named
> checkpoints).
>
> Older: `TextView-2026-08-12-v2.zip` — same-day refresh: panel
> resizing overhauled for real — dividers track the mouse 1:1 all the way to
> the actual limit (a feedback loop capped drags at HALF the available space),
> panels never auto-shrink (a too-small shoulder scrolls instead), and the
> file tree's private minimum is gone (one floor for every panel). Plus: the
> Git panel no longer shows another session's repo, and the markdown Split
> preview lives inside the tab under its own toolbar (no stray header/✕).
>
> Older: `TextView-2026-08-12.zip` — the tab strip now lives INSIDE the
> pane — always. The window-level tab bar is gone: tabs, the `+` button, and the
> per-tab toolbar start at the pane's edge (right of the tool windows), exactly
> like split panes; the header row above is purely sessions. Tab→session-pill
> drag works from any pane's strip; tabs scroll to the selected chip. Includes
> the v3 pane fixes below.
>
> Older: `TextView-2026-08-11-v3.zip` — pane fixes over v2: the session
> tab strip stays visible while split (it was being composited over), the file
> navigator/footer/watcher follow every pane interaction, and right-clicking any
> tab offers **Split Pane Right / Left** (tear the tab into a new pane; drag a
> tab onto the other pane's strip to move it). Title band: flat tone, pills
> clear of the traffic lights.
>
> Older: `TextView-2026-08-11-v2.zip` — the panes debut. Highlights since
> the morning build: **editor panes** — split the window into panes (right or down),
> each with its own tab strip, drag tabs between panes, click anywhere to focus a
> pane, resize panes on a visible gutter, every pane carries its own
> breadcrumb + Render|Split|Editor|HEX toolbar for ITS tab, and pane layouts
> persist per session (split, quit, reopen — it all comes back); ⌥⌘` cycles pane
> focus. Plus: fast close/quit/session-switch can no longer lose your last
> keystrokes (editor flush handshake), the markdown Split preview lives inside its
> tab, and links are first-class everywhere — absolute file/folder paths open
> in-app and `other.md#section` jumps to the heading.
>
> Older: `TextView-2026-08-11.zip` — same date, pre-panes. Highlights since 2026-08-05: the left
> tool-window column rebuilt on one rule (uniform panels, resizes that take from the
> neighbor then the flexible panel — never push chrome; visible gutter bars with grab
> pills; drags glued to the pointer with self-healing stored heights), bottom tool
> windows as TABS with one resizable band, the terminal demoted to a regular tool
> window (dock it anywhere, ⌃` toggles, open panes migrate), dock placement remembered
> app-globally, search results grouped honestly with folder hints + click lands on the
> matched word, hex editor visible caret + hex↔ascii tandem selection, split preview
> readable in dark themes, session-switch feedback (instant press + progress HUD),
> concise value-only footer with relative-date toggle, accent-tinted active tab/rows,
> centered traffic lights + title-band depth gradient.
>
> Older: `TextView-2026-08-05.zip` — pointer-glued panel resizing, predictable cursors,
> false disk-conflicts eliminated, bounded commit diffs, wikilinks, named session save
> points, Git Status Diff|Source toggle, Local History per-hunk merge, per-file detected
> indentation, purple find matches + match ruler, crash-guard "Restore Now".
>
> Older: `TextView-2026-07-31.zip` — LaTeX math (backend MathML), footnotes/alerts/
> definition lists, WebView git-diff viewer, split mode, tab/session drag, 3-way
> disk-conflict merge, Mermaid 11.16.0, bundled license notices. Self-contained
> (`--verify-resources` packaging gate); runs on any Apple-Silicon Mac (macOS 15+).
>
> The `2026-06-25` / `2026-06-25-v2` builds are known-broken off the build machine
> (resource-path packaging defect, fixed in `2026-06-26-packagingfix`).

| Artifact | Build | Arch | Signing |
|---|---|---|---|
| `TextView-<date>.zip` | **release / prod** | `arm64` (Apple Silicon) | self-signed `MarkdownViewer Local Dev`, hardened runtime |

Verify a download: `shasum -c TextView-<date>.zip.sha256`

## Install on another Mac (Apple Silicon)

1. Unzip → `TextView.app`.
2. It's self-signed (not notarized), so Gatekeeper blocks the first launch. Clear quarantine:
   ```sh
   xattr -dr com.apple.quarantine /path/to/TextView.app
   ```
   (or right-click the app in Finder → **Open**, once).
3. On first run, re-grant any Privacy & Security permissions you need (Full Disk Access, Screen Recording) — TCC grants don't transfer between machines.

## Notes
- **Want to build it yourself?** Clone the source archive —
  <https://github.com/josangel555/textview_archive> — and run
  `bash scripts/build-app.sh release` (macOS 15+, Xcode 16+/Swift 6, stable Rust).
  No signing identity needed; the archive's README covers the Gatekeeper steps.
- **arm64 only** — won't run on Intel Macs (that would need a universal/x86_64 build).
- **Not notarized** (no Apple Developer ID yet), which is why the quarantine step is required.
- These are binary artifacts; git history grows ~14 MB per dated zip. If this repo gets large, consider GitHub Releases or Git LFS instead of committing zips directly.
