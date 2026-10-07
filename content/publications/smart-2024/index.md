---
title: Towards Automated Visual Inspection of Electrical Grid Assets for the Smart Grid - An Application to HV Insulators
authors:
  - Fernando Lopes
  - me
  - André Coelho

author_notes:
  - ""
date: '2024-09-17'
publishDate: '2024-11-04'
publication_types:
  - paper-conference
publication:
  name: 2024 IEEE International Conference on Communications, Control, and Computing Technologies for Smart Grids
  short_name: SmartGridComm 2024
peer_reviewed: true
open_access: false
license: IEEE Copyright
awards:
  - name: ""
    level: ""
    note: ""
funding:
  - funder: Fundaçãao para a Ciência e a Tecnologia
    grant: UIDB/50008/2020 – https://doi.org/10.54499/UIDB/50008/2020
abstract: |
  The globally growing demand for electric power requires extensive upgrades in Transport and Distribution systems, yet the reliability of ageing infrastructure remains the more critical concern, with power line insulators accounting for over 50% of maintenance costs. This research evaluates deep learning computer vision for automated visual inspection of electrical grid assets with real-world data, detecting defects in HV disc insulators in visible-light images with two state-of-the-art models. YOLOv8s achieved a mAP@50 of 87.9%, while Faster R-CNN X101-FPN achieved 87.2%. Assessing the performance and complexity of data-driven inspection techniques is a first step toward streamlined models for real-time operation and integration in smart grid monitoring and control, or as a component of a grid digital twin.
summary: YOLOv8s vs Faster R-CNN for HV insulator defect detection, reaching 87.9% and 87.2% mAP50 on real-world data.
tags:
  - Asset inspection
  - HV insulator
  - Computer vision
  - Deep learning
  - Smart grid
featured: false
hugoblox:
  ids:
    # arxiv: ""
    doi: 10.1109/SmartGridComm60555.2024.10738034
links:
  - type: pdf
    url: paper_SmartGridComm24_An_Application_to_HV_Insulators.pdf
  #- type: code
  #  url: ""
  #- type: dataset
  #  url: ""
  #- type: poster
  #  url: ""
  #- type: project
  #  url: ""
  #- type: slides
  #  url: ""
  #- type: source
  #  url: ""
  #- type: video
  #  url: ""
image:
  caption: "One-stage vs two-stage detectors for automated HV insulator inspection."
  focal_point: ""
  preview_only: true
projects: []
slides: ""
status: published
---
<!-- Add the paper text or supplementary notes. Markdown, math, and code are supported. -->
---

## Overview

<!-- TODO: drop your file in as graphical_abstract.pdf -->
<figure>
  <iframe
    src="graphical_abstract.pdf#toolbar=0&view=Fit&navpanes=0"
    width="100%"
    style="aspect-ratio: 1/0.99; border: none;">
    <p>
      This browser does not support PDFs. Please download the PDF to view it:
      <a href="graphical_abstract.pdf">Download PDF</a>.
    </p>
  </iframe>

  <figcaption>
  One-stage (YOLOv8s) vs two-stage (Faster R-CNN X101-FPN) detectors on HV insulator defects.
  </figcaption>
</figure>

First-step evaluation toward low-complexity models for smart grid integration, comparing two state-of-the-art object detectors on high-resolution HV insulator imagery (Oslo, Norway).

### Background

- Power demand doubling by 2050; T&D expansion beyond 160 million km
- Insulators are 5-8% of installation cost but over 50% of maintenance expenses
- Utilities collect large visual datasets; human interpretation is the bottleneck
- Aerial in-person inspection costs 150-800 C/km vs 40-150 C/km automated

### Challenges

- Public IDID contains 1,600 annotated files but only 400 unique images (mirrored copies)
- Random validation splits leak mirrored copies; missing annotations (edge-cropped, adjacent good discs)
- Small defective features in high-resolution UAV imagery with intricate backgrounds
- Models must generalize to unseen test data and other collections (e.g. EDP MV lines)

### Approach

- One-stage YOLOv8s (1024px input, 100 epochs, batch 32) vs two-stage Faster R-CNN X101-FPN
- Classes: functional (good), defective disc (broken), defective shell (flashover)
- Careful 15% validation split excluding mirrored training copies
- Test inference on 88 non-annotated IDID images plus 24 EDP LabElec MV images

<!-- TODO: drop your file in as approach.png -->
<figure>
  <img src="approach.png" alt="Detection pipeline. " width="100%">
  <figcaption>
  Automated inspection pipeline from UAV imagery to localized defect predictions.
  </figcaption>
</figure>

### Data

- **Dataset**
  - IDID (EPRI): 1,600 files, 17,116 instances (78% good, 15% flashover, 7% broken)
  - 400 unique images; validation carefully split to avoid mirrored leakage
  - Test: 88 IDID images plus 24 private EDP MV-line images

<!-- TODO: drop your file in as data.png -->
<figure>
  <img src="data.png" alt="Dataset examples and splits. " width="100%">
  <figcaption>
  Dataset examples, annotation gaps, and split organization.
  </figcaption>
</figure>

### Results

- YOLOv8s mAP50 of 87.9% (good 92.9%, broken 82.7%, flashover 88.0%)
- Faster R-CNN mAP50 of 87.2% (good 94.3%, broken 83.0%, flashover 84.2%)
- YOLO converges with best validation at epoch 56 (early stop at 71); broken class conservative but precise
- YOLO generalizes better to blurred EDP images; Faster struggles off-focus and on glass insulators

<!-- TODO: drop your file in as results.png -->
<figure>
  <img src="results.png" alt="Quantitative and qualitative results. " width="100%">
  <figcaption>
  Training curves, confusion matrices, and correct vs mispredicted examples.
  </figcaption>
</figure>

### Findings

- Both models perform well for a fully automated approach; YOLO leads on box regression, Faster on some classification
- Annotation trustworthiness bounds metric reliability (mAP50-95 decay, background confusion)
- Mispredictions cluster on bird droppings, occlusions, evening light, and unseen glass insulators
- Next steps: high-quality dataset, domain-specific architectures, low-complexity edge models

---

## Conference Paper

<iframe
  src="paper_SmartGridComm24_An_Application_to_HV_Insulators.pdf#toolbar=0&view=Fit&navpanes=0"
  width="100%"
  style="aspect-ratio: 1 / 1.294; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="paper_SmartGridComm24_An_Application_to_HV_Insulators.pdf">Download PDF</a>.
  </p>
</iframe>

---
