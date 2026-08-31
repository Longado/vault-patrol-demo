# Vault patrol report

- vault: `/tmp/patrol-posvl3bf`
- anchor commit: `1325c2ab5fb8a7f978c5ec06f6914c6e064ed858`
- model: `gemini-3.5-flash` · prompt: `2026-08-30.5`
- mechanical findings: 4 · semantic findings kept: 7 · dropped by verification: 1 (counter_evidence_missing 1)
- model calls: 1 · notes too large to send: 0

Subtraction only: this PR deletes dead index lines and proposes edits. Nothing new is created.

| category | file | evidence | proof in other note | related | action | why |
|---|---|---|---|---|---|---|
| `broken_link` | `MEMORY.md` | `(notes/planner_2025.md)` | — | notes/planner_2025.md | **delete_line** | Index links to a file that does not exist; a dead index entry misleads every reader. |
| `orphan` | `notes/orphan_scratch.md` | `# Scratch  Random thoughts from a 2026-03 session. Nothing links here.` | — | — | **needs_human** | File exists but nothing in the vault points to it; unreachable notes are a dead lake. |
| `dangling_wikilink` | `notes/planning_v1.md` | `[[planning-v2]]` | — | — | **needs_human** | [[wikilink]] points at a note that does not exist (may be a planned note; flagged, not deleted). |
| `dangling_wikilink` | `tools/stack.md` | `[[tasks-db]]` | — | — | **needs_human** | [[wikilink]] points at a note that does not exist (may be a planned note; flagged, not deleted). |
| `stale_active_reference` | `tools/stack.md` | `For semantic search across all notes, use the Memvid MCP server (see [[memvid]]).` | `notes/changelog.md`: `2026-07-03: Memvid MCP server removed from settings.json — the configured path no longer exists. Not live.` | — | **delete_line** | The tool stack note instructs the reader to use the Memvid MCP server for semantic search, but the changelog note states that this server was removed and is no longer live. |
| `stale_active_reference` | `tools/stack.md` | `For nightly full-text indexing of every note, run the llm-wiki daemon; it is the search backend.` | `notes/changelog.md`: `2026-07-03: llm-wiki daemon retired.` | — | **delete_line** | The tool stack note instructs the reader to run the llm-wiki daemon for nightly full-text indexing, but the changelog note states that this daemon has been retired. |
| `stale_active_reference` | `tools/memvid.md` | `Call `memvid.search` for any semantic lookup.` | `notes/changelog.md`: `2026-07-03: Memvid MCP server removed from settings.json — the configured path no longer exists. Not live.` | — | **mark_historical** | The Memvid MCP server note instructs the reader to call memvid.search for semantic lookup, but the changelog note states that the server was removed and is no longer live. |
| `pinned_old_version` | `tools/llm_starter.md` | `MODEL = "claude-3-5-sonnet-20240620"  # always use this model` | — | — | **needs_human** | The LLM call starter boilerplate note hard-codes an old model ID (claude-3-5-sonnet-20240620) with an explicit instruction to always use it, despite the vault's current date being in late 2026. |
| `hard_conflict` | `notes/testing.md` | `Every change must ship with tests. No production code without a failing test first, no exceptions.` | `notes/coding_style.md`: `Trivial one-line changes need no test; YAGNI applies to tests too.` | — | **add_arbitration_line** | The testing rules note states that every change must ship with tests with no exceptions, while the coding style note directly contradicts this by stating that trivial one-line changes need no test. |
| `falsified_claim` | `tools/recall.md` | `Used daily; it has become the default way to find cross-project code.` | `notes/recall_log.md`: `Measured real usage via shell history: 1 invocation in 17 days.` | — | **delete_line** | The recall tool note claims that the tool is used daily and has become the default way to find cross-project code, but the recall experiment log shows that it was only invoked once in 17 days. |
| `falsified_claim` | `tools/stack.md` | `it is used daily and replaced manual grep.` | `notes/recall_log.md`: `Measured real usage via shell history: 1 invocation in 17 days.` | — | **delete_line** | The tool stack note claims that the recall tool is used daily, but the recall experiment log shows that it was only invoked once in 17 days. |
