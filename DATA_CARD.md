# Bayan NLP — Data Card

## Dataset Overview

The Bayan NLP project uses small educational datasets created for demonstrating and evaluating bilingual Arabic-English NLP tasks.

The datasets support:

- Topic Classification
- Sentiment Classification
- Named Entity Recognition
- Extractive Question Answering
- Semantic Search

## Languages

- Arabic
- English

The project includes both monolingual and cross-lingual examples to evaluate bilingual behavior.

## Data Usage

Data is divided into training, validation, and test examples where required by the task.

The validation data is used for model selection and threshold calibration, while test data is reserved for final evaluation.

## Task Data

### Classification

The classification data contains Arabic and English text examples with labels for topic and sentiment experiments.

### Named Entity Recognition

NER examples use BIO-style labels to represent entity boundaries and entity types.

Subword alignment is applied when tokenized words are split into multiple transformer tokens.

### Question Answering

QA examples contain:

- Question
- Context
- Answer span
- No-answer cases

These examples are used to evaluate extractive span selection and no-answer handling.

### Semantic Search

The retrieval dataset contains bilingual documents and queries.

It includes:

- Arabic queries
- English queries
- Cross-lingual retrieval examples
- No-answer queries

## Data Quality Considerations

The datasets are intentionally small because the project focuses on demonstrating the complete NLP workflow rather than building a production-scale model.

This affects the stability and generalization of the measured results, particularly for NER and QA.

## Privacy and Safety

The project data is used for educational experimentation and does not intentionally include sensitive personal information.

## Limitations

- Small sample sizes
- Limited linguistic diversity
- Limited entity examples
- Limited QA examples
- Results should not be generalized to production data without additional evaluation
