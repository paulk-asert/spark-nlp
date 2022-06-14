---
layout: docs
header: true
seotitle: Spark NLP
title: Spark NLP release notes 3.6.0
permalink: /docs/en/spark_ocr_versions/release_notes_3_6_0
key: docs-release-notes
modify_date: "2022-01-06"
show_nav: true
sidebar:
    nav: sparknlp
---

## 3.6.0

Release date: 05-08-2021

#### Overview

Handwritten detection and visualization improvement.


#### New Features

* Added [ImageHandwrittenDetector](ocr_object_detection#imagehandwrittendetector) for detecting 'signature', 'date', 'name',
 'title', 'address' and others handwritten text.
* Added rendering labels and scores in [ImageDrawRegions](ocr_pipeline_components#imagedrawregions).
* Added possibility to scale image to fixed size in [ImageScaler](ocr_pipeline_components#imagescaler)
 with keeping original ratio.


#### Enhancements

* Support new version of pip for installing python package
* Added support string labels for detectors
* Added an auto inferencing of the input shape for detector models
* New license validator


#### Bugfixes

* Fixed display BGR images in display functions


#### New and updated notebooks

* [Image Signature Detection example](https://github.com/JohnSnowLabs/spark-ocr-workshop/blob/3.6.0/jupyter/SparkOcrImageSignatureDetection.ipynb)
* [Image Handwritten Detection example](https://github.com/JohnSnowLabs/spark-ocr-workshop/blob/3.6.0/jupyter/SparkOcrImageHandwrittenDetection.ipynb)
* [Image Scaler example](https://github.com/JohnSnowLabs/spark-ocr-workshop/blob/3.6.0/jupyter/SparkOcrImageScaler.ipynb)

<div class="prev_ver h3-box" markdown="1">

## Versions

</div>

<ul class="pagination">
    <li>
        <a href="release_notes_3_5_0">Version 3.5.0</a>
    </li>
    <li>
        <strong>Version 3.6.0</strong>
    </li>
    <li>
        <a href="release_notes_3_7_0">Version 3.7.0</a>
    </li>
</ul>

<ul class="pagination pagination_big">
  <li><a href="release_notes_3_12_0">3.12.0</a></li>
  <li><a href="release_notes_3_11_0">3.11.0</a></li>
  <li><a href="release_notes_3_10_0">3.10.0</a></li>
  <li><a href="release_notes_3_9_1">3.9.1</a></li>
  <li><a href="release_notes_3_9_0">3.9.0</a></li>
  <li><a href="release_notes_3_8_0">3.8.0</a></li>
  <li><a href="release_notes_3_7_0">3.7.0</a></li>
  <li class="active"><a href="release_notes_3_6_0">3.6.0</a></li>
  <li><a href="release_notes_3_5_0">3.5.0</a></li>
  <li><a href="release_notes_3_4_0">3.4.0</a></li>
  <li><a href="release_notes_3_3_0">3.3.0</a></li>
  <li><a href="release_notes_3_2_0">3.2.0</a></li>
  <li><a href="release_notes_3_1_0">3.1.0</a></li>
  <li><a href="release_notes_3_0_0">3.0.0</a></li>
  <li><a href="release_notes_1_11_0">1.11.0</a></li>
  <li><a href="release_notes_1_10_0">1.10.0</a></li>
  <li><a href="release_notes_1_9_0">1.9.0</a></li>
  <li><a href="release_notes_1_8_0">1.8.0</a></li>
  <li><a href="release_notes_1_7_0">1.7.0</a></li>
  <li><a href="release_notes_1_6_0">1.6.0</a></li>
  <li><a href="release_notes_1_5_0">1.5.0</a></li>
  <li><a href="release_notes_1_4_0">1.4.0</a></li>
  <li><a href="release_notes_1_3_0">1.3.0</a></li>
  <li><a href="release_notes_1_2_0">1.2.0</a></li>
  <li><a href="release_notes_1_1_2">1.1.2</a></li>
  <li><a href="release_notes_1_1_1">1.1.1</a></li>
  <li><a href="release_notes_1_1_0">1.1.0</a></li>
  <li><a href="release_notes_1_0_0">1.0.0</a></li>
</ul>