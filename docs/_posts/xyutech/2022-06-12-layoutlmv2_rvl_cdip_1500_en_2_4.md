---
layout: model
title: LayoutLMv2 model trained on RVL-CDIP subset for visual document classification
author: John Snow Labs
name: layoutlmv2_rvl_cdip_1500
date: 2022-06-12
tags: [en, licensed]
task: OCR Document Classification
language: en
edition: Spark OCR 3.4.0
spark_version: 2.4
supported: true
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

This model uses LayoutLMv2 to classify documents. It was trained on subset of RVL-CDIP dataset.

## Predicted Entities



{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/clinical/ocr/layoutlmv2_rvl_cdip_1500_en_3.4.0_2.4_1655011402997.zip){:.button.button-orange.button-orange-trans.arr.button-icon}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
        binary_to_image = BinaryToImage() \
            .setOutputCol("image") \
            .setImageType(ImageType.TYPE_3BYTE_BGR)

        img_to_hocr = ImageToHocr() \
            .setInputCol("image") \
            .setOutputCol("hocr") \
            .setIgnoreResolution(False) \
            .setOcrParams(["preserve_interword_spaces=0"])

        tokenizer = HocrTokenizer() \
            .setInputCol("hocr") \
            .setOutputCol("token")

        doc_class = VisualDocumentClassifierV2() \
            .pretrained("layoutlmv2_rvl_cdip_1500", "en", "clinical/ocr") \
            .setInputCols(["token", "image"]) \
            .setOutputCol("label")

        pipeline = PipelineModel(stages=[
            binary_to_image,
            img_to_hocr,
            tokenizer,
            doc_class,
        ])
```
```scala
    var bin2imTransformer = new BinaryToImage()
    bin2imTransformer.setImageType(ImageType.TYPE_3BYTE_BGR)

    val ocr = new ImageToHocr()
      .setInputCol("image")
      .setOutputCol("hocr")
      .setIgnoreResolution(false)
      .setOcrParams(Array("preserve_interword_spaces=0"))

    val tokenizer = new HocrTokenizer()
      .setInputCol("hocr")
      .setOutputCol("token")

    val visualDocumentClassifier = VisualDocumentClassifierv2
        .pretrained("layoutlmv2_rvl_cdip_1500", "en", "clinical/ocr")
        .setInputCols(Array("token", "image"))

    val pipeline = new Pipeline()
      .setStages(Array(
        bin2imTransformer,
        ocr,
        tokenizer,
        visualDocumentClassifier
      ))
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|layoutlmv2_rvl_cdip_1500|
|Type:|ocr|
|Compatibility:|Spark OCR 3.4.0+|
|License:|Licensed|
|Edition:|Official|
|Language:|en|
|Size:|1.1 GB|

## References

RVL-CDIP (Ryerson Vision Lab Complex Document Information Processing) dataset consisting of 400 000 grayscale images in 16 classes