---
layout: model
title: XLM-RoBERTa Base, CoNLL-03 NER Pipeline
author: ahmedlone127
name: xlm_roberta_base_token_classifier_conll03_pipeline
date: 2022-06-14
tags: [open_source, ner, token_classifier, xlm_roberta, conll03, xlm, base, en]
task: Named Entity Recognition
language: en
edition: Spark NLP 4.0.0
spark_version: 3.0
supported: false
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

This pretrained pipeline is built on the top of [xlm_roberta_base_token_classifier_conll03](https://nlp.johnsnowlabs.com/2021/10/03/xlm_roberta_base_token_classifier_conll03_en.html) model.

## Predicted Entities



{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/community.johnsnowlabs.com/ahmedlone127/xlm_roberta_base_token_classifier_conll03_pipeline_en_4.0.0_3.0_1655217192119.zip){:.button.button-orange.button-orange-trans.arr.button-icon}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python

pipeline = PretrainedPipeline("xlm_roberta_base_token_classifier_conll03_pipeline", lang = "en")

pipeline.annotate("My name is John and I work at John Snow Labs.")
```
```scala

val pipeline = new PretrainedPipeline("xlm_roberta_base_token_classifier_conll03_pipeline", lang = "en")

pipeline.annotate("My name is John and I work at John Snow Labs.")
```
</div>

## Results

```bash

+--------------+---------+
|chunk         |ner_label|
+--------------+---------+
|John          |PERSON   |
|John Snow Labs|ORG      |
+--------------+---------+
```

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|xlm_roberta_base_token_classifier_conll03_pipeline|
|Type:|pipeline|
|Compatibility:|Spark NLP 4.0.0+|
|License:|Open Source|
|Edition:|Community|
|Language:|en|
|Size:|851.9 MB|

## Included Models

- DocumentAssembler
- SentenceDetectorDLModel
- TokenizerModel
- XlmRoBertaForTokenClassification
- NerConverter
- Finisher