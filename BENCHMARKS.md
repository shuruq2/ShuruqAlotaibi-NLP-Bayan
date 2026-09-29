# Bayan NLP — Benchmarks

## 1. Benchmark Objective

The optimization benchmark compares the actual `PROJECT_ARTIFACT` across PyTorch and optimized ONNX inference.

The main measurement is P95 inference latency.

## 2. Latency Results

| Backend | P95 Latency |
|---|---:|
| PyTorch | 986.71 ms |
| ONNX INT8 | 149.89 ms |

ONNX INT8 provided a significant latency improvement compared with the PyTorch reference.

## 3. Quality Check

Optimization was also evaluated for prediction consistency.

| Metric | Result |
|---|---:|
| INT8 Prediction Agreement | 0.875 |
| Changed Predictions | 12.5% |
| Quality Tax | 12.5% |

Although INT8 was faster, it changed some predictions compared with the reference model.

## 4. Rollback Decision

The optimization decision considers both latency and prediction quality.

Final decision:

**Chosen backend: PyTorch**

The INT8 model was not selected as the final backend because the measured prediction agreement did not satisfy the quality requirement.

This demonstrates the rollback rule: a faster model is not automatically selected when the optimization introduces an unacceptable quality change.

## 5. Service Validation

The inference service was tested with:

- Arabic input
- English input
- Invalid input

The tests verify that the service can process bilingual requests and reject invalid input through a consistent interface.

## 6. Benchmark Limitations

Results are specific to the tested runtime and benchmark workload. Latency may differ across hardware and deployment environments.
