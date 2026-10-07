# AstaBrief 8B on Runpod Serverless

[![Runpod](https://api.runpod.io/badge/runpod-workers/astabrief)](https://console.runpod.io/hub/runpod-workers/astabrief)

Serve AstaBrief 8B (Allen AI) on Runpod Serverless with vLLM.
License: apache-2.0.

## Recipe

| Setting | Value |
|---|---|
| Engine | vllm |
| Image | `runpod/worker-v1-vllm:v2.27.0` |
| GPU | 1x RTX 4090 |
| Precision | bf16 |
| Max model length | 8192 |

## Environment

| Variable | Value |
|---|---|
| `GPU_MEMORY_UTILIZATION` | `0.90` |
| `MAX_CONCURRENCY` | `30` |
| `MAX_MODEL_LEN` | `8192` |
| `MODEL_NAME` | `allenai/AstaBrief_8B` |
| `TENSOR_PARALLEL_SIZE` | `1` |

## Measured performance and cost

| GPU | Serverless $/hr | TTFT ms | tok/s | $/1M output tokens |
|---|---|---|---|---|
| 1x RTX 4090 bf16 (this recipe) | $1.10 | 216.1 | 56.2 | $5.44 |
| 1x RTX 4090 fp8 | $1.10 | 210.3 | 77.6 | $3.94 |

Cost per 1M output tokens is the hourly rate divided by measured throughput. It
assumes one saturated worker and no idle time, so treat it as a floor.

## Deploy links

- Deploy on Runpod: https://console.runpod.io/hub/runpod-workers/astabrief?utm_source=hub&utm_medium=product&utm_campaign=202610_activation_indie-ml-dev_allen-ai-astabrief-8b&utm_content=readme

The link carries `utm_campaign=202610_activation_indie-ml-dev_allen-ai-astabrief-8b`. Keep it intact when you copy a link anywhere else.
