---
title: Automated Defect Detection in Electroluminescence Imaging of PV Cells Using Deep Learning
authors:
  - me
  - Inácio Fonseca
  - Fernando Lopes

author_notes:
  - ""
date: 2024-10-25
publishDate: 2024-10-25
publication_types:
  - paper-conference
publication:
  name: 2024 Portuguese Conference on Pattern Recognition
  short_name: RecPad 2024
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
  Maintaining photovoltaic system efficiency requires monitoring the integrity of PV modules and cells, since some defects remain hidden while visible imperfections may not affect performance. Electroluminescence imaging highlights non-uniform areas revealing subtle defects, but traditionally relies on manual specialist inspection. This work classifies PV cell operational conditions from EL imagery with a VGG19 model, achieving AUC values of 0.95, 0.94, and 0.90 for poly, mono, and mixed datasets respectively. Results demonstrate the potential of deep learning for automated PV cell inspection using EL imagery, with greater efficiency but limitations such as data scarcity.
summary: Classifying PV cell condition from electroluminescence imagery with VGG19, reaching 0.90-0.95 AUC across mono, poly, and mixed sets.
tags:
  - Photovoltaic inspection
  - Electroluminescence imaging
  - Deep learning
  - VGG19
  - Defect classification
featured: false
hugoblox:
  ids:
    # arxiv: ""
    # doi: ""
links:
  - type: pdf
    url: paper_RecPad2024_PV_Cells_Pedro_Daniel_Rocha.pdf
  #- type: code
  #  url: ""
  #- type: dataset
  #  url: ""
  - type: poster
    url: poster_RecPad2024_PV_Cells_Pedro_Daniel_Rocha.pdf
  #- type: project
  #  url: ""
  #- type: slides
  #  url: ""
  #- type: source
  #  url: ""
  #- type: video
  #  url: ""
image:
  caption: "Automated defect detection in electroluminescence imaging of PV cells."
  focal_point: ""
  preview_only: false
projects: []
slides: ""
status: published
---
<!-- Add the paper text or supplementary notes. Markdown, math, and code are supported. -->
---

## Overview

Binary classification of functional vs defective PV cells from electroluminescence images with a fine-tuned VGG19, evaluated separately on monocrystalline, polycrystalline, and mixed sets from the public ELPV dataset.

---

## Conference Poster

<iframe
  src="poster_RecPad2024_PV_Cells_Pedro_Daniel_Rocha.pdf#toolbar=0&view=Fit&navpanes=0"
  width="100%"
  style="aspect-ratio: 1 / 1.414; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="poster_RecPad2024_PV_Cells_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---

## Conference Paper

<iframe
  src="paper_RecPad2024_PV_Cells_Pedro_Daniel_Rocha.pdf#toolbar=0&view=Fit&navpanes=0"
  width="100%"
  style="aspect-ratio: 1 / 1.414; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="paper_RecPad2024_PV_Cells_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---
