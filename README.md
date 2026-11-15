# TextView — distribution bundles

Pre-built **release (production)** builds of TextView (MarkdownViewer), one zip per date.

**Source code:** the complete development history is published as a read-only archived
snapshot at **<https://github.com/josangel555/textview_archive>** (MIT) — every commit,
not maintained (no issues/PRs), but it builds into a runnable app with one command
(`bash scripts/build-app.sh release`; see its README). Product page:
<https://josangel.com/textview/>.

> **Use `TextView-2026-11-15.zip`** (latest) — the first build **signed with an
> Apple Developer ID and notarized by Apple**: unzip, move it to Applications,
> open it, and confirm macOS's one-time "downloaded from the Internet — Apple
> checked it for malicious software" prompt. No quarantine commands, no System
> Settings → "Open Anyway". Also new since 2026-11-11: **undo survives
> switching sessions** — come back to a file and ⌘Z picks up where you left
> off (kept for the app's lifetime, as long as the text is unchanged). Each
> build now carries its own build number (this one: 3869).
>
> Older: `TextView-2026-11-11.zip` (self-signed). Highlights since 2026-08-27:
> **unsaved edits now survive switching sessions and coming back** (a
> background autosave could erase the edit of a tab that hadn't loaded yet —
> fixed, for text and HEX edits); **markdown links can point at a line**
> (`[x](/path/to/server.ts:1889)`, `:LINE:COL`, `#L42` open the file at that
> line); **web pages can no longer load inside the app** (link clicks go to
> your browser; drops/redirects are blocked and audit-logged);
> **count lines of code** from the folder-stats card (committed-only,
> CLOC-style, plus commit Activity); **crowded tabs show file names** with
> dividers between tabs and a Settings → Appearance → Tab Icons option;
> markdown opens Rendered again; Show Unsaved Changes on the dirty dot;
> deleted files' Local History browsable without recreating; a crash in the
> Claude Code (MCP) bridge fixed.
>
> Older: `TextView-2026-08-27.zip` — the panes-polish wave. The app
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
| `TextView-<date>.zip` from **2026-11-15** | **release / prod** | `arm64` (Apple Silicon) | **Developer ID Application, notarized by Apple, ticket stapled**, hardened runtime |
| `TextView-<date>.zip` up to 2026-11-11 | release / prod | `arm64` | self-signed `MarkdownViewer Local Dev`, hardened runtime (not notarized) |

Verify a download: `shasum -c TextView-<date>.zip.sha256`

## Install on another Mac (Apple Silicon)

1. Unzip → `TextView.app`, and move it to **Applications** (running it straight from
   Downloads works, but macOS then runs it from a temporary read-only location).
2. Open it. macOS asks once: *"TextView" is an app downloaded from the Internet. Are you
   sure you want to open it? … Apple checked it for malicious software and none was
   detected.* → **Open**. The approval is stapled to the app, so this works offline too.
3. macOS asks for folder access (Documents, Desktop, Downloads) the first time TextView
   reads there; grant whatever else you use (e.g. Full Disk Access) in System Settings →
   Privacy & Security — permissions don't transfer between machines.

Check a copy yourself: `spctl --assess --type execute -vv /Applications/TextView.app` →
`accepted`, `source=Notarized Developer ID`.

**Builds up to 2026-11-11 are self-signed** (not notarized), so macOS 15+ blocks their
first launch; clear the quarantine flag once before opening:
```sh
xattr -dr com.apple.quarantine /path/to/TextView.app
```

## Notes
- **Want to build it yourself?** Clone the source archive —
  <https://github.com/josangel555/textview_archive> — and run
  `bash scripts/build-app.sh release` (macOS 15+, Xcode 16+/Swift 6, stable Rust).
  No signing identity needed; the archive's README covers the Gatekeeper steps.
- **arm64 only** — won't run on Intel Macs (that would need a universal/x86_64 build).
- **Notarized since 2026-11-15** (Developer ID + Apple's notary service). A build you make
  yourself from the archive is unsigned/locally signed — fine on the Mac that built it.
- These are binary artifacts; git history grows ~14 MB per dated zip. If this repo gets large, consider GitHub Releases or Git LFS instead of committing zips directly.
