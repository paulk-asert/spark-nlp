---
layout: model
title: Portuguese BioBERT Embeddings (from pucpr)
author: John Snow Labs
name: biobert_embeddings_all
date: 2022-04-11
tags: [biobert, embeddings, pt, open_source]
task: Embeddings
language: pt
edition: Spark NLP 3.4.2
spark_version: 3.0
supported: true
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BioBERT Embeddings model, uploaded to Hugging Face, adapted and imported into Spark NLP. `biobertpt-all` is a Portuguese model orginally trained by `pucpr`.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/biobert_embeddings_all_pt_3.4.2_3.0_1649685875871.zip){:.button.button-orange.button-orange-trans.arr.button-icon}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
documentAssembler = DocumentAssembler() \    
    .setInputCol("text") \    
    .setOutputCol("document")

tokenizer = Tokenizer() \
    .setInputCols("document") \
    .setOutputCol("token")
  
embeddings = BertEmbeddings.pretrained("biobert_embeddings_all","pt") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("embeddings")
    
pipeline = Pipeline(stages=[documentAssembler, tokenizer, embeddings])

data = spark.createDataFrame([["Odeio o cancro"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler() 
      .setInputCol("text") 
      .setOutputCol("document")
 
val tokenizer = new Tokenizer() 
    .setInputCols(Array("document"))
    .setOutputCol("token")

val embeddings = BertEmbeddings.pretrained("biobert_embeddings_all","pt") 
    .setInputCols(Array("document", "token")) 
    .setOutputCol("embeddings")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, embeddings))

val data = Seq("Odeio o cancro").toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|biobert_embeddings_all|
|Compatibility:|Spark NLP 3.4.2+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[sentence, token]|
|Output Labels:|[bert]|
|Language:|pt|
|Size:|667.7 MB|
|Case sensitive:|true|

## References

- https://huggingface.co/pucpr/biobertpt-all
- https://aclanthology.org/2020.clinicalnlp-1.7/
- https://github.com/HAILab-PUCPR/BioBERTpt