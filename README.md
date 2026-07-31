# TextView — distribution bundles

Pre-built **release (production)** builds of TextView (MarkdownViewer), one zip per date.

> **Use `TextView-2026-07-31.zip`** (latest). Highlights since 2026-06-26: LaTeX math
> (backend MathML — works in export, no JS), markdown footnotes / GitHub alerts /
> definition lists, a WebView git-diff viewer, split edit+preview mode, tab & session
> drag-reorder + drag-a-tab-onto-a-session-pill, recently-closed tabs (⇧⌘T), 3-way
> disk-conflict merge that never silently discards a side, Local History size caps with
> smart thinning, Mermaid 11.16.0 (security advisories cleared), bundled third-party
> license notices, and crash/data-safety hardening. Self-contained (`--verify-resources`
> packaging gate) and runs on any Apple-Silicon Mac (macOS 15+).
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
