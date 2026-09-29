# Bayan NLP — Evaluation Report

## 1. Evaluation Approach

The project evaluates multiple bilingual NLP tasks using fixed test examples and task-appropriate metrics. Results are reported as measured, including unsuccessful experiments.

## 2. Classification

Topic and sentiment classification were evaluated using Macro-F1.

| Task | Macro-F1 |
|---|---:|
| Topic Classification | 0.1000 |
| Sentiment Classification | 0.4286 |

The results show that classification performance remains limited on the current small dataset.

## 3. Named Entity Recognition

NER was evaluated at entity level in addition to token-level checks.

| Metric | Result |
|---|---:|
| Entity F1 | 0.0000 |

The model did not correctly recover complete entities in the final evaluation set. This highlights entity boundary and generalization errors as areas for improvement.

## 4. Question Answering

The extractive QA system was evaluated for answer-span extraction and no-answer handling.

| Metric | Result |
|---|---:|
| Exact Match | 0.0000 |
| No-answer Accuracy | 0.0000 |

The final evaluation indicates that both span selection and no-answer calibration require further improvement.

## 5. Semantic Search

Retrieval was evaluated using ranking metrics and bilingual queries.

| Metric | Result |
|---|---:|
| Recall@3 | 1.0000 |
| MRR@3 Before Re-ranking | 0.6667 |
| MRR@3 After Re-ranking | 0.7222 |
| Cross-lingual Test | PASS |
| Retrieval No-answer Test | PASS |

Cross-encoder re-ranking improved MRR from 0.6667 to 0.7222.

## 6. Error Analysis

The evaluation process identified several recurring error categories:

- Classification errors between related classes.
- NER entity-boundary and entity-detection errors.
- QA incorrect span selection.
- QA false answers for no-answer questions.
- Retrieval ranking errors where the relevant document is retrieved but not ranked first.

These errors were used to identify areas for future improvement.

## 7. Prioritized Improvements

### Priority 1 — QA Calibration
Improve no-answer threshold calibration and include additional no-answer examples.

### Priority 2 — NER
Increase annotated NER data and improve entity-boundary learning.

### Priority 3 — Classification
Increase balanced bilingual training examples and evaluate class-level performance.

## 8. Evaluation Limitations

The evaluation datasets are intentionally small and educational. Therefore, the reported metrics demonstrate the implemented evaluation pipeline and should not be interpreted as production-level performance.
