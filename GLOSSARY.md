# Week-One Glossary

Ten terms that come up in the first week of using Claude Code on an empirical project. One plain definition each, and one line on why it matters for research work. Pairs with the walkthrough at https://tooearlytosay.com/research/methodology/first-session-claude-code/

**commit** · A saved snapshot of the project at a point in time, recorded by git with a short message saying what changed.
*Why an economist cares:* a commit right after each working result is a natural capture point, and it makes any past state of the analysis recoverable when a later change breaks something.

**diff** · The line-by-line difference between two versions of a file: what was added, what was removed.
*Why an economist cares:* reading the diff is how AI-written changes to cleaning and estimation code get reviewed before they are trusted.

**PR (pull request)** · A proposed batch of commits packaged for review before it merges into the main line of the project.
*Why an economist cares:* a coauthor or advisor can read exactly what changed in the analysis, comment on it, and approve it before it becomes the record.

**.gitignore** · A text file listing what git must never track: data files, credentials, caches, generated output.
*Why an economist cares:* it keeps restricted-use microdata and API keys out of a repository that may one day ship publicly as a replication package.

**DuckDB** · A database engine that runs inside a script or notebook, with no server to install, and queries files directly with SQL.
*Why an economist cares:* it aggregates a multi-gigabyte administrative extract on a laptop without loading the whole file into memory.

**parquet** · A compressed, column-oriented file format for tabular data.
*Why an economist cares:* it preserves column types between sessions, so FIPS codes saved as strings stay strings, and large panels load in a fraction of CSV time.

**FIPS** · Federal Information Processing Standards codes: the numeric identifiers for states (2 digits), counties (5), and census tracts (11).
*Why an economist cares:* FIPS codes are the merge keys of US regional data, and they carry leading zeros, so storing them as integers silently corrupts every merge downstream.

**context window** · The bounded amount of text a model can consider at once; every file the agent reads and every exchange in the session consumes part of it.
*Why an economist cares:* the window is a budget. Reading ten files costs more than deeply analyzing one, and a filled window is why an agent starts forgetting what was said ten minutes ago.

**subagent** · A helper the agent creates with its own separate context window; it explores or executes a focused task and reports back a summary.
*Why an economist cares:* it works like delegating a retrieval task to a research assistant: the dead ends stay in the helper's workspace, and only the summary lands in the main session.

**compaction** · The automatic summarization Claude Code performs when a session nears its context limit, replacing older conversation with a condensed summary.
*Why an economist cares:* summaries lose nuance. The decision survives compaction; the three reasons an alternative was rejected may not, which is why decisions belong in notes files that persist.
