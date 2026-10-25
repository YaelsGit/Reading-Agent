# Reading Agent: API vs SDK

## Project
A personal reading-list agent implemented using two harnesses:
- `API/`: a custom harness over the Anthropic Messages API.
- `SDK/`: an implementation using the Claude Agent SDK.
- `shared/`: shared tools and persisted domain data.

## Offline tests
The latest offline test run passed: 12 tests.

These tests validate mocked behavior and local state handling. They do not establish real-model behavior or measured API-versus-SDK performance.

## Implementation size

### API harness
| File | Lines |
|---|---:|
| caching.py | 34 |
| compaction.py | 53 |
| context.py | 37 |
| history.py | 80 |
| loop.py | 61 |
| memory.py | 61 |
| tokens.py | 69 |
| tools.py | 101 |
| __init__.py | 5 |
| **Total** | **501** |

## Runtime measurements

Real API and SDK scenario runs have not been completed. Therefore, token usage, cache hit rate, model-call counts, cost, elapsed time, and scenario pass rates are not yet available for a fair comparison.

No measured values are fabricated in this report.

## Comparison and discussion

The custom API harness provides direct control over the tool loop, message history, context construction, caching breakpoints, compaction, and token accounting. This control also requires maintaining and testing each component.

The SDK delegates more harness behavior to Claude Code and the SDK runtime, potentially reducing custom implementation effort. The trade-off is less direct control over internal orchestration and the need to measure actual runtime behavior before drawing quantitative conclusions.

## Limitations and remaining work

- Run the same scenario with both implementations using the same model and effort.
- Save the resulting reports as `results/api.json` and `results/sdk.json`.
- Add the measured comparison table, cache percentages, tool usage, costs, and pass/fail checks.
- Complete the SDK-side lines-of-code comparison.
- Verify that all API runtime actions print the responsible filename.
- Confirm that the external-tool requirement is satisfied by the implementation and the assignment rubric.

## Conclusion

The offline test suite passes, but the quantitative comparison and final performance conclusions remain incomplete until real scenario results are available.
