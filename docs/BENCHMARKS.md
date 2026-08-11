# Internal Benchmark Evidence

This comparison documents two prior internal runs supplied by Giangero Studio: a baseline before the finished delegation workflow and a benchmark using the workflow. An intermediate setup/tuning attempt was intentionally excluded because it was not a valid comparison run.

The results are evidence that the workflow produced the intended role separation in the recorded benchmark. They are not a general model-quality, cost, latency, or efficiency benchmark.

![Token allocation before and after the delegation workflow](../assets/benchmark-token-allocation.svg)

## Comparison task

Both displayed runs used the same bounded Unity editor task. The task was to:

- add a small editor-only Asset Diagnostics menu command;
- log the Unity version and valid counts of Scene, Prefab, and C# script assets;
- inspect existing editor utilities and follow their location, namespace, style, and menu conventions;
- use Unity Editor tooling to recompile, inspect the Console, execute the menu command, and verify every reported count;
- keep the change minimal and avoid gameplay, networking, scenes, prefabs, packages, and runtime behavior;
- report changed files, tools, validation, actual output, and remaining risks or unrelated Console errors.

Project names, local paths, and private source details have been omitted from this public description.

## Token allocation

| Run | Sol | Luna | Combined | Sol share | Luna share |
|---|---:|---:|---:|---:|---:|
| Without finished delegation workflow | 1.94M | 1.81M | 3.75M | 51.7% | 48.3% |
| **With delegation workflow** | **403,852** | **4,230,396** | **4,634,248** | **8.7%** | **91.3%** |

The baseline counts were recorded in rounded millions. The workflow benchmark used exact token counts.

## Workflow benchmark responsibility separation

| Activity | Sol Medium | Luna XHIGH |
|---|---:|---:|
| Tokens | **403,852** | **4,230,396** |
| Project read/review calls | 1 small final diff | 13 |
| Unity MCP calls | **0** | **36** |
| Coding | No | Yes |
| Compilation/refresh | No | Yes |
| Console inspection | No | Yes |
| Menu execution | No | Yes |
| Independent count testing | No | Yes |
| Validation retries | No | Yes |

Combined workflow benchmark usage was **4,634,248 tokens**.

## What the workflow benchmark demonstrates

- Sol stayed in the coordinator/reviewer role and inspected only one small final diff.
- Sol performed no Unity MCP calls, implementation, compilation, Console inspection, menu execution, independent count testing, or validation retries.
- Luna performed the complete production and validation loop, including 36 Unity MCP calls and all repair iterations.
- The observed responsibility split closely matches the intended Sol-orchestrator/Luna-executor ownership model.

## Methodology and limitations

- The figures come from prior internal runs and have not been independently reproduced for this repository.
- The baseline token counts are rounded to two decimal places in millions.
- The workflow benchmark token and call counts are exact as recorded by the author.
- The intermediate setup/tuning attempt is excluded and is not presented as benchmark evidence.
- Elapsed time, monetary cost, full acceptance criteria, and raw logs are not currently published.
- Token allocation alone does not establish output quality. The strongest evidence is the accompanying activity split showing which agent performed implementation and validation.
- Results may vary with Codex version, model availability, prompts, tools, repository size, and task complexity.

Future benchmark updates should publish repeatable scenarios, environment/version information, acceptance criteria, and raw or redacted logs where practical.
