---
layout: model
title: Detect Living Species(w2v_cc_300d)
author: John Snow Labs
name: ner_living_species
date: 2022-06-22
tags: [es, ner, clinical, licensed]
task: Named Entity Recognition
language: es
edition: Spark NLP for Healthcare 3.5.3
spark_version: 3.0
supported: true
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Extract living species from clinical texts in Spanish which is critical to scientific disciplines like medicine, biology, ecology/biodiversity, nutrition and agriculture. This model is trained using `w2v_cc_300d` embeddings.

It is trained on the [LivingNER](https://temu.bsc.es/livingner/) corpus that is composed of clinical case reports extracted from miscellaneous medical specialties including COVID, oncology, infectious diseases, tropical medicine, urology, pediatrics, and others.

## Predicted Entities

`HUMAN`, `SPECIES`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
[Open in Colab](https://colab.research.google.com/github/JohnSnowLabs/spark-nlp-workshop/blob/master/tutorials/Certification_Trainings/Healthcare/1.Clinical_Named_Entity_Recognition_Model.ipynb){:.button.button-orange.button-orange-trans.co.button-icon}
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/clinical/models/ner_living_species_es_3.5.3_3.0_1655907754521.zip){:.button.button-orange.button-orange-trans.arr.button-icon}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
document_assembler = DocumentAssembler()\
    .setInputCol("text")\
    .setOutputCol("document")

sentence_detector = SentenceDetectorDLModel.pretrained("sentence_detector_dl", "xx")\
    .setInputCols(["document"])\
    .setOutputCol("sentence")

tokenizer = Tokenizer() \
    .setInputCols(["sentence"])\
    .setOutputCol("token")

embeddings = WordEmbeddingsModel.pretrained("w2v_cc_300d","es")\
    .setInputCols(["sentence", "token"]) \
    .setOutputCol("embeddings")

ner_model = MedicalNerModel.pretrained("ner_living_species", "es","clinical/models")\
    .setInputCols(["sentence", "token", "embeddings"])\
    .setOutputCol("ner")

ner_converter = NerConverter()\
    .setInputCols(["sentence", "token", "ner"])\
    .setOutputCol("ner_chunk")

pipeline = Pipeline(stages=[
    document_assembler, 
    sentence_detector,
    tokenizer,
    embeddings,
    ner_model,
    ner_converter   
    ])

model = pipeline.fit(spark.createDataFrame([[""]]).toDF("text"))

data = spark.createDataFrame([["""Lactante varón de dos años. Antecedentes familiares sin interés. Antecedentes personales: Embarazo, parto y periodo neonatal normal.En seguimiento por alergia a legumbres , diagnosticado con diez meses por reacción urticarial generalizada con lentejas y garbanzos ,con dieta de exclusión a legumbres desde entonces. En ésta visita la madre describe episodios de eritema en zona maxilar derecha con afectación ocular ipsilateral que se resuelve en horas tras la administración de corticoides. Le ha ocurrido en 5-6 ocasiones ,en relación con la ingesta de alimentos previamente tolerados. No refiere transgresiones dietéticas ni reacción accidental con legumbres. Exploración complementaria: Cacahuete, ac(ige)19.2 Ku.arb/l; lentejas 39.6 Ku.arb/l. Resultados: Ante la sospecha clínica de Síndrome de Frey, se tranquiliza a los padres , explicándoles la naturaleza del cuadro y se cita para revisión anual."""]]).toDF("text")

result = model.transform(data)
```
```scala
val document_assembler = new DocumentAssembler()
    .setInputCol("text")
    .setOutputCol("document")

val sentence_detector = SentenceDetectorDLModel.pretrained("sentence_detector_dl", "xx")
    .setInputCols("document")
    .setOutputCol("sentence")

val tokenizer = new Tokenizer()
    .setInputCols("sentence")
    .setOutputCol("token")

val embeddings = WordEmbeddingsModel.pretrained("w2v_cc_300d","es")
    .setInputCols(Array("sentence", "token"))
    .setOutputCol("embeddings")

val ner_model = MedicalNerModel.pretrained("ner_living_species", "es","clinical/models")
    .setInputCols(Array("sentence", "token", "embeddings"))
    .setOutputCol("ner")

val ner_converter = new NerConverter()
    .setInputCols(Array("sentence", "token", "ner"))
    .setOutputCol("ner_chunk")

val pipeline = new PipelineModel().setStages(Array(document_assembler, 
                                                  sentence_detector,
                                                  tokenizer,
                                                  embeddings,
                                                  ner_model,
                                                  ner_converter))

val data = Seq("""Lactante varón de dos años. Antecedentes familiares sin interés. Antecedentes personales: Embarazo, parto y periodo neonatal normal.En seguimiento por alergia a legumbres , diagnosticado con diez meses por reacción urticarial generalizada con lentejas y garbanzos ,con dieta de exclusión a legumbres desde entonces. En ésta visita la madre describe episodios de eritema en zona maxilar derecha con afectación ocular ipsilateral que se resuelve en horas tras la administración de corticoides. Le ha ocurrido en 5-6 ocasiones ,en relación con la ingesta de alimentos previamente tolerados. No refiere transgresiones dietéticas ni reacción accidental con legumbres. Exploración complementaria: Cacahuete, ac(ige)19.2 Ku.arb/l; lentejas 39.6 Ku.arb/l. Resultados: Ante la sospecha clínica de Síndrome de Frey, se tranquiliza a los padres , explicándoles la naturaleza del cuadro y se cita para revisión anual.""").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

## Results

```bash
+--------------+-------+
|ner_chunk     |label  |
+--------------+-------+
|Lactante varón|HUMAN  |
|familiares    |HUMAN  |
|personales    |HUMAN  |
|neonatal      |HUMAN  |
|legumbres     |SPECIES|
|lentejas      |SPECIES|
|garbanzos     |SPECIES|
|legumbres     |SPECIES|
|madre         |HUMAN  |
|legumbres.    |SPECIES|
|Cacahuete     |SPECIES|
|lentejas      |SPECIES|
|padres        |HUMAN  |
+--------------+-------+
```

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|ner_living_species|
|Compatibility:|Spark NLP for Healthcare 3.5.3+|
|License:|Licensed|
|Edition:|Official|
|Input Labels:|[sentence, token, embeddings]|
|Output Labels:|[ner]|
|Language:|es|
|Size:|15.1 MB|

## References

[https://temu.bsc.es/livingner/](https://temu.bsc.es/livingner/)

## Benchmarking

```bash
 label         precision  recall  f1-score  support 
 B-HUMAN       1.00       1.00    1.00      3281    
 B-SPECIES     1.00       1.00    1.00      3712    
 I-HUMAN       1.00       0.99    0.99      297     
 I-SPECIES     0.90       0.99    0.95      1732    
 micro-avg     0.98       1.00    0.99      9022    
 macro-avg     0.97       0.99    0.98      9022    
 weighted-avg  0.98       1.00    0.99      9022   
```