# Bayan NLP — Model Card

## Model Overview

Bayan is an educational bilingual Arabic-English NLP project developed as part of the SDAIA Academy NLP program.

The project demonstrates multiple NLP tasks within one workflow, including classification, NER, question answering, semantic search, evaluation, optimization, and serving.

## Supported Languages

- Arabic
- English

## NLP Tasks

- Topic Classification
- Sentiment Classification
- Named Entity Recognition
- Extractive Question Answering
- Bilingual Semantic Search

## Evaluation Summary

| Component | Result |
|---|---:|
| Topic Macro-F1 | 0.1000 |
| Sentiment Macro-F1 | 0.4286 |
| NER Entity F1 | 0.0000 |
| QA Exact Match | 0.0000 |
| QA No-answer Accuracy | 0.0000 |
| Retrieval Recall@3 | 1.0000 |
| Retrieval MRR Before Re-ranking | 0.6667 |
| Retrieval MRR After Re-ranking | 0.7222 |

## Optimization

The project artifact was evaluated using PyTorch and ONNX INT8 inference.

| Backend | P95 Latency |
|---|---:|
| PyTorch | 986.71 ms |
| ONNX INT8 | 149.89 ms |

INT8 prediction agreement was 0.875, corresponding to a measured 12.5% quality tax on the benchmark workload.

Because the optimized model changed predictions beyond the accepted quality requirement, PyTorch was retained as the final backend.

## Intended Use

The project is intended for:

- Educational NLP experimentation
- Arabic-English NLP demonstrations
- Evaluation of NLP pipelines
- Semantic retrieval experiments
- Model optimization experiments

## Limitations

The models were trained and evaluated using small educational datasets.

Current limitations include:

- Weak NER generalization
- Weak QA span extraction
- Weak QA no-answer handling
- Limited classification performance
- Performance measurements depend on the runtime environment

The system should not be treated as a production-ready NLP service.

## Responsible Use

Model predictions may be incorrect and should not be used for high-stakes decisions without additional validation and testing.
