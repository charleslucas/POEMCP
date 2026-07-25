# Changelog

All notable changes to **poe-data-mcp** are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

> **Releasing:** move the accumulated `[Unreleased]` entries into a new
> `## [x.y.z] - YYYY-MM-DD` section, commit, then
> `git tag vx.y.z && git push origin vx.y.z`. The tag drives the published
> version and this section becomes the GitHub Release notes automatically.

## [Unreleased]

## [0.3.1] - 2026-07-25

### Fixed
- **YouTube fetch reliability** — pin to reliable player clients and surface partial output on
  timeout instead of failing outright (`fetch_youtube_transcript` / `fetch_youtube_description`).

## [0.3.0] - 2026-07-11

### Added
- **`parse_pob_skill_groups`** — extract the structured socket/link groups from a
  PoB export code or share URL (pobb.in / poedb.tw / pastebin), per skill set.
  Returns JSON: every link group with its gems (name, skillId, level, quality,
  support and main-skill flags), `gem_count`, and the item `slot` binding when the
  author set one (unassigned groups are item-agnostic — the link group is the unit).
  For slot-bound groups it also returns `item_sockets`: the item's **actual** socket
  colour layout (e.g. `B-G-R-B-B-B`), read straight from the export. Complements
  `parse_pob` (prose summary of only the active set) for gem-to-socket / required-
  colour reconstruction; derive per-gem colours via pob-mcp's `get_gem_detail`.

## [0.2.0] - 2026-07-11

### Changed
- Renamed the package from `poemcp` to **`poe-data-mcp`** — a descriptive name
  distinct from the sibling `poe-trade-mcp`. This covers the PyPI distribution,
  the import package (`poe_data_mcp`), the console script (`poe-data-mcp`), and
  the registry entry (`io.github.charleslucas/poe-data-mcp`).
- Cache environment variable `POEMCP_CACHE_DIR` → `POE_DATA_MCP_CACHE_DIR`, and
  the default cache directory `<user-cache>/poemcp` → `<user-cache>/poe-data-mcp`.

### Deprecated
- The old `poemcp` name (PyPI `poemcp` 0.1.1 and registry
  `io.github.charleslucas/poemcp`) is deprecated in favour of `poe-data-mcp`.

## [0.1.1] - 2026-07-11

_Published under the original name `poemcp` (now deprecated; superseded by 0.2.0)._

### Added
- Initial public release: an MCP server for Path of Exile game-data lookups —
  wiki pages, gems, unique items, passive nodes, item modifiers, maps, scarabs,
  live prices (poe.ninja), Craft of Exile mod pools, and Path of Building export
  parsing. No API key required.
- `poe_mcp_suite_info` tool and server `instructions` announcing the wider
  poe_mcp_suite, so any MCP-compatible agent can discover and install it.
- Packaged for ephemeral runners (`uvx` / `pipx`) and published to PyPI and the
  MCP registry via tag-triggered GitHub Actions Trusted Publishing (OIDC).
- Craft of Exile cache resolves to a shared platform user-cache dir, overridable
  via an environment variable.

[Unreleased]: https://github.com/charleslucas/poe-data-mcp/compare/v0.3.0...HEAD
[0.3.0]: https://github.com/charleslucas/poe-data-mcp/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/charleslucas/poe-data-mcp/compare/v0.1.1...v0.2.0
[0.1.1]: https://github.com/charleslucas/poe-data-mcp/releases/tag/v0.1.1
