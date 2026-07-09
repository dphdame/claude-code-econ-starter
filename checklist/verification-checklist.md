# Verification Checklist for AI-Assisted Empirical Work

One page. Run it before any result, citation, or claim is treated as final. Each item is pass or fail; a skipped item is a fail.

The framing: the agent satisfies this checklist before a human reads the output. A clean run is where trust starts, never where it ends.

Why these items: https://tooearlytosay.com/research/methodology/verification-tax/ and https://tooearlytosay.com/research/methodology/validate-ai-econometric-code/

## A. Citations

| # | Check | Pass/Fail |
|---|-------|-----------|
| 1 | Every citation was fetched from its source, never accepted from generation: the DOI or URL resolves | |
| 2 | Author names and title match the fetched source exactly | |
| 3 | Journal, year, volume, and pages match the fetched source | |
| 4 | The claim attributed to each paper appears in that paper | |

Unchecked citations accumulate hallucination debt: one fabricated reference becomes the foundation for claims built on top of it, and unwinding the stack costs far more than the check would have.

## B. Code and estimators: the planted-truth routine

| # | Check | Pass/Fail |
|---|-------|-----------|
| 5 | The estimand is written down from the paper or canonical implementation before reading the generated code | |
| 6 | The low-visibility choices are named in the spec: comparison set, weighting, transformation window, indexing | |
| 7 | A controlled data-generating process exists with a planted true value for the target parameter | |
| 8 | The implementation recovers the planted value across many simulated draws, within a stated tolerance | |
| 9 | The simulated data break the easy symmetries (unequal group sizes, unbalanced timing, missing cells), so weighting and aggregation mistakes surface | |
| 10 | The code was read line by line against the source on every weight, aggregation rule, and index; some errors appear only in the reading, never in the simulation output | |

The validate-estimator skill in this kit walks an agent through items 5 through 10.

## C. Empirical claims

| # | Check | Pass/Fail |
|---|-------|-----------|
| 11 | Every number in prose traces to a computed value in a saved output file | |
| 12 | Every factual claim about external data names its source, and the source says what the claim says | |
| 13 | Anything to be published or shared externally received the highest scrutiny; internal notes and formatting may pass on review alone | |

## Recording

Date each run. Keep the filled checklist next to the results it gates, so the verification travels with the output.
