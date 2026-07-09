# [Project name]

[One sentence: what this project estimates or measures, on what data. Example: Estimates the effect of SNAP outreach on enrollment using a county panel, 2015-2023.]

Why these sections: https://tooearlytosay.com/research/methodology/claude-md-research-context/

## Data conventions

- Geographic identifiers: [example: census tracts as 11-digit FIPS codes stored as strings, never integers]
- Coordinates: [example: WGS84 (EPSG:4326), decimal degrees, unprojected]
- Canonical analysis file: [path and row count, example: data/processed/analysis_panel.csv (4,847 rows)]
- Units: [example: dollars are nominal unless the variable name ends in _real]
- Missing values: [example: NaN everywhere; or a sentinel such as -999, and which scripts expect it]

These conventions prevent a specific class of errors: dropped leading zeros on FIPS codes, silently reprojected coordinates, statistics computed over sentinel values.

## File organization

- Raw data: data/raw/ (never modify)
- Processed data: data/processed/ (intermediate outputs)
- Final outputs: data/output/ (results for publication)
- Scripts: [naming rule, example: numbered by execution order, 01_, 10_, 20_]

## Current analysis focus

- Working on: [the current question or specification]
- Current script: [path]
- Key hypothesis: [one line]
- Known open issue: [one line]

Update this section whenever the analysis phase changes; it is the section that goes stale fastest.

## Known pitfalls

- [An edge case discovered through debugging, and the required handling. Example: some rural tracts have zero grocery stores within 60 minutes by transit; code them as NA, never as the maximum time.]
- [API rate limits, data vintages, merge gotchas. Example: Census 2020 geometries with ACS 2023 5-year estimates; the vintage mismatch is accepted.]

## Verification expectations

Every citation, estimator, and empirical claim gets checked before it is treated as final. The checks live in verification-checklist.md (copied from this kit's checklist/ folder into the project); run them before presenting results. AI-generated estimator code is assumed to contain plausible-looking errors until it recovers a planted known answer.

## Session end

Before ending a session, capture what changed, why, what failed, and what comes next (about five minutes; the session-notes skill from this kit does it). Then update the "Current analysis focus" section above.

## What NOT to put in this file

- Entire data processing pipelines (those belong in scripts)
- Statistical methods in detail (those belong in the README or the paper)
- Every variable definition (the codebook carries those)

This file holds the unwritten conventions applied when writing code for this project. The test: anything explained to the agent in three consecutive sessions belongs here.
