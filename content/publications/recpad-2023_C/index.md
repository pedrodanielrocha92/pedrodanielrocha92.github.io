---
title: Deep Vision Quality Control - An Example Application in the Casting Industry
authors:
  - me
  - Nuno Martins
  - Fernando Lopes
  - Luís Cruz

author_notes:
  - ""
date: 2023-10-27T14:00:00Z
publishDate: 2023-10-27T14:00:00Z
publication_types:
  - paper-conference
publication:
  name: 2023 Portuguese Conference on Pattern Recognition
  short_name: RecPad 2023
peer_reviewed: true
open_access: true
license: CC-BY-4.0
awards:
  - name: ""
    level: ""
    note: ""
funding:
  - funder: Fundaçãao para a Ciência e a Tecnologia
    grant: UIDB/50008/2020 – https://doi.org/10.54499/UIDB/50008/2020
abstract: |
  Ensuring the quality of individual parts during manufacturing upholds final product integrity and customer confidence, yet manual inspection is time-consuming and variable. This paper explores deep learning classification of manufactured parts as defective or non-defective from grayscale images, experimenting on a public dataset of 1,300 cast submersible pump impellers with a custom Keras CNN. It attains 94% recall on the defective class and 89% precision on the non-defective class (97% AUC-ROC), complemented by Grad-CAM insights into the model's decisions.
summary: Custom CNN quality control on cast impeller images, with 94% defective recall and 97% AUC-ROC.
tags:
  - Quality control
  - Casting industry
  - Convolutional neural networks
  - Grad-CAM
  - Defect classification
featured: false
hugoblox:
  ids:
    # arxiv: ""
    # doi: ""
links:
  - type: pdf
    url: paper_RECPAD23_Casting_Pedro_Daniel_Rocha.pdf
  #- type: code
  #  url: ""
  #- type: dataset
  #  url: ""
  - type: poster
    url: poster_RECPAD23_Casting_Pedro_Daniel_Rocha.pdf
  #- type: project
  #  url: ""
  #- type: slides
  #  url: ""
  #- type: source
  #  url: ""
  #- type: video
  #  url: ""
image:
  caption: "Deep vision quality control on cast submersible pump impellers."
  focal_point: ""
  preview_only: false
projects: []
slides: ""
status: published
---
<!-- Add the paper text or supplementary notes. Markdown, math, and code are supported. -->
---

## Overview

Custom Keras CNN for binary quality control of cast submersible pump impellers from grayscale images, trained on the original 512px split after the augmented set showed integrity issues, with Grad-CAM decision analysis.

---

## Conference Poster

<iframe
  src="poster_RECPAD23_Casting_Pedro_Daniel_Rocha.pdf#toolbar=0&view=Fit&navpanes=0"
  width="100%"
  style="aspect-ratio: 1 / 1.414; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="poster_RECPAD23_Casting_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---

## Conference Paper

<iframe
  src="paper_RECPAD23_Casting_Pedro_Daniel_Rocha.pdf#toolbar=0&view=Fit&navpanes=0"
  width="100%"
  style="aspect-ratio: 1 / 1.414; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="paper_RECPAD23_Casting_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---
