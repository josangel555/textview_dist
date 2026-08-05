# TextView — distribution bundles

Pre-built **release (production)** builds of TextView (MarkdownViewer), one zip per date.

> **Use `TextView-2026-08-05.zip`** (latest). Highlights since 2026-07-31: panel/column
> resizing glued to the pointer (the half-speed flicker/lag class is fixed everywhere),
> predictable pointer cursors, false "file changed on disk" conflicts eliminated, huge
> commit diffs bounded (no more wedged git panel), wikilinks + working relative links,
> named session save points, Git Status Diff|Source toggle with ephemeral opens + visible
> diff line washes/edge bars, Local History per-hunk "Merge into Current" + Copy Version,
> per-file detected indentation (guides/Tab match the file), purple find matches with a
> scrollbar match ruler + zoom-scaled find bar, restyled tabs (active connects to the
> document), crash-guard "Restore Now", doubled recents, hex hot-exit.
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
- **arm64 only** — won't run on Intel Macs (that would need a universal/x86_64 build).
- **Not notarized** (no Apple Developer ID yet), which is why the quarantine step is required.
- These are binary artifacts; git history grows ~14 MB per dated zip. If this repo gets large, consider GitHub Releases or Git LFS instead of committing zips directly.
