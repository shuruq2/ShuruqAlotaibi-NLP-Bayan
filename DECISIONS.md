# Bayan NLP — Technical Decisions

## 1. Bilingual Text Processing

Bayan supports Arabic and English text. Arabic preprocessing was designed to normalize text while preserving information required by downstream NLP tasks.

Arabic-specific processing and golden tests were included to verify expected preprocessing behaviour.

## 2. Classification

The project evaluates topic and sentiment classification using baseline and transformer-based approaches.

Macro-F1 was selected as a primary metric because it reflects performance across multiple classes rather than relying only on overall accuracy.

Final measured transformer results include:

- Topic Macro-F1: 0.10
- Sentiment Macro-F1: 0.4286

The transformer models were not required to outperform the baseline; results are reported as measured.

## 3. Named Entity Recognition

NER uses BIO tagging with subword alignment.

Both token-level and entity-level evaluation were performed.

Final entity-level performance:

- Entity F1: 0.00

The result indicates that the current NER model does not generalize reliably on the evaluation set. The result is retained as evidence rather than replaced or hidden.

## 4. Extractive Question Answering

The QA component uses extractive span prediction and includes no-answer handling.

Final evaluation showed:

- Exact Match: 0.00
- No-answer Accuracy: 0.00

No-answer calibration therefore remains a known limitation of the current QA implementation.

## 5. Bilingual Semantic Search

Multilingual sentence embeddings were used with a FAISS index for bilingual semantic retrieval.

Measured retrieval results:

- MRR before re-ranking: 0.6667
- MRR after cross-encoder re-ranking: 0.7222

Cross-encoder re-ranking was retained because it produced a measurable improvement in retrieval ranking.

The retrieval evaluation also includes cross-lingual and no-answer cases.

## 6. Optimization and Rollback

The actual PROJECT_ARTIFACT was benchmarked before and after optimization.

Measured P95 latency:

- PyTorch: 986.71 ms
- ONNX INT8: 149.89 ms

INT8 produced substantially lower latency, but prediction agreement with the reference model was:

- Prediction agreement: 0.875
- Quality tax: 12.5%

Because optimization changed predictions beyond the accepted quality requirement, the final serving decision was:

**Chosen backend: PyTorch**

This demonstrates the project's rollback rule: an optimization is not automatically deployed only because it is faster.

## 7. Measured Extension

An Arabic normalization ablation was implemented as the bounded project extension.

Retrieval performance:

- Raw-text MRR: 0.6667
- CAMeL-normalized MRR: 0.6667

The extension did not improve retrieval quality and introduced additional processing cost.

Decision: retain the simpler retrieval preprocessing configuration because the measured extension did not provide a quality benefit.

## 8. Main Limitations

- Small educational datasets limit generalization.
- NER performance remains weak.
- QA span prediction and no-answer handling require further improvement.
- Optimization results depend on the execution environment.
- INT8 improved latency but introduced a measurable prediction quality tax.
