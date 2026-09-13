# Results summary and provenance

## Track A: deterministic allocation mechanisms

- 1,800 simulated tasks across 15 independently held-out layouts.
- Dynamic restricted rules versus greedy reduced the deadline-miss rate by 0.05237 on average; all 15 layouts improved and the Holm-adjusted one-sided p-value was 0.00012207.
- The corresponding mean differences were -0.02521 for low-reserve starts, -0.05096 for moving-congestion exposure, and -0.11623 for low-friction exposure.
- All prespecified non-inferiority guardrails passed.
- Stage B recorded 160,219 attempts, six retained timeouts, and zero fallbacks.

These are measured outputs of the frozen warehouse simulator, not physical-warehouse observations.

## Track G: DeepSeek symbolic grounding

- 3,882 held-out events produced 6,102 profile-eligible responses.
- Equal-map-family semantic exactness was 99.52% for facts and 93.02% for restricted rules.
- Moving-congestion restricted rules reached 69.53% semantic exactness; erroneous proposals were rejected fail-closed.

## Track E: matched cached-DeepSeek simulation

- 60 matched simulated episodes across 15 layouts.
- No hard violation, pending cargo, solver fallback, or solver timeout occurred.
- DeepSeek restricted rules passed all three frozen non-inferiority components against deterministic restricted rules.
- Low-friction exposure decreased in all 15 layouts relative to DeepSeek facts, with a mean paired difference of -0.14725 ticks per completed cargo and an exact one-sided p-value of 3.0517578125e-5.

## API-service measurements

- 8,919 real DeepSeek API calls.
- Median latency 1,544.83 ms; p95 2,211.11 ms; p99 2,619.32 ms.
- 18 invalid response records and 22,867,094 total tokens.

API latency, token usage, and model responses are measured service outputs. Warehouse performance remains simulated.
