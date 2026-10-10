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
  The globally growing demand for electric power, projected to double by 2050, requires extensive upgrades in Transport and Distribution (T&D) systems. Despite the need for new infrastructures to address this demand, the reliability of ageing electrical T&D systems remains a more critical concern, where power line insulators account for over 50% of T&D maintenance costs. To boost inspection efficiency, electric utilities are integrating remote inspection technologies into their operations. However, the processing of the growing volume of collected data is currently strongly limited by human interpretation tasks.This research evaluates the performance of computer vision based on deep learning models for automated visual inspection of electrical grid assets, validated with real-world data. The developed work presents an example application of automated visual inspection of HV insulators, detecting defects in disc insulators in visible light images, using two state-of-the-art deep learning models. YOLOv8s achieved a mAP@50 of 87.9%, while Faster R-CNN X101-FPN achieved 87.2% for the same metric. The findings highlight the advantages and limitations of automated visual inspection, enabling utility companies to benefit from higher efficiency inspection processes, reducing the costs and improving the reliability of electrical grid maintenance.Assessing the performance and complexity of data-driven automated visual inspection techniques is crucial for developing streamlined models that effectively handle high data volumes, and that can evolve to real-time operation and integration in the monitoring and control functions of the smart grid or as a dynamic component of a digital twin of the grid.
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

> **Copyright notice:** © 2024 IEEE. Personal use of this material is permitted. Permission from IEEE must be obtained for all other uses. The published version is available via [IEEE Xplore](https://doi.org/10.1109/SmartGridComm60555.2024.10738034).

---

## Overview

First-step evaluation toward low-complexity models for smart-grid integration. Two state-of-the-art detectors are compared on high-resolution HV-insulator imagery: one-stage YOLOv8s vs two-stage Faster R-CNN X101-FPN.

### Data

- **IDID (EPRI):** 1,600 files, 17,116 instances (78% good, 15% flashover, 7% broken), but only 400 unique images plus mirrored copies.
- Validation split carefully separated (15%) to avoid mirrored leakage between train and valid.
- Edge-cropped discs and good discs adjacent to broken ones are often not annotated, which bounds metric reliability.

<figure>
  <img src="figures/miss_annotations.jpg" alt="IDID example with missing annotations on edge-cropped and adjacent discs." width="100%">
  <figcaption>
  IDID annotation gaps: edge-cropped discs and adjacent good discs left unannotated.
  </figcaption>
</figure>

### Experiment

- Early comparative experiment, no novel method — off-the-shelf detectors with standard training:
  - YOLOv8s, 1024px input, 100 epochs, batch 32, default Ultralytics augmentation.
  - Faster R-CNN X101-FPN, short edge 640–800px, batch 4 images, default Detectron2 augmentation.
- Classes: good (functional), broken (defective disc), flashover (defective shell).
- Extra qualitative test on 88 non-annotated IDID images plus 24 private EDP MV-line images.

### Results

- Validation mAP50: YOLOv8s 87.9% (good 92.9%, broken 82.7%, flashover 88.0%) vs Faster R-CNN 87.2% (good 94.3%, broken 83.0%, flashover 84.2%).
- YOLO converges with best validation at epoch 56 (early stop at 71); box loss improves only slightly from pre-trained weights, class attribution improves most.
- Faster leads slightly on classification for good/broken, YOLO leads on box regression (mAP50-95 decay) and generalizes better to blurred EDP images.

<figure>
  <img src="figures/training_loss_hvi.png" alt="YOLOv8s training and validation loss curves." width="100%">
  <figcaption>
  YOLOv8s training dynamics: box and classification loss, train vs valid. Valid stalls after epoch 56.
  </figcaption>
</figure>

<figure>
  <img src="figures/results_hvi.png" alt="YOLOv8s precision, recall, F1 and precision-recall curves." width="100%">
  <figcaption>
  YOLOv8s validation curves. Broken is conservative but precise (high precision, lower recall); good has highest recall.
  </figcaption>
</figure>

<figure>
  <img src="figures/cm_hvi.png" alt="YOLOv8s confusion matrices, absolute and normalized." width="100%">
  <figcaption>
  Confusion at 0.25 confidence. Many good predictions on background might reflect missing annotations rather than pure false positives.
  </figcaption>
</figure>

### Qualitative check

- Both models detect functional and defective discs in most test images.
- Typical YOLO confusions: bird droppings vs flashover, occlusions, defocus treated as background, unseen glass insulators.
- Faster struggles more off-focus and in evening light; both show duplicate boxes with different labels on the same object.

<figure>
  <img src="figures/yolo_vs_faster.jpg" alt="Side-by-side YOLOv8s (top) and Faster R-CNN (bottom) predictions." width="100%">
  <figcaption>
  Same scenes, top YOLOv8s vs bottom Faster R-CNN. On the left, YOLO detects a flashover and a broken disc that Faster misses. On the right, YOLO misses several broken discs that Faster detects.
  </figcaption>
</figure>


### Takeaways

- Both detectors are viable for a fully automated first pass; YOLO is the more practical baseline for edge / real-time use.
- Metric reliability is bounded by annotation trustworthiness (missing boxes, coarse geometry).
- Next steps from this early experiment: high-quality dataset, domain-specific architectures, low-complexity edge models.

---

## Conference Paper

A self-archived accepted manuscript is provided below. <br>
The published version is available in [IEEE Xplore](https://doi.org/10.1109/SmartGridComm60555.2024.10738034).

<iframe
  src="paper_SmartGridComm24_An_Application_to_HV_Insulators.pdf#toolbar=0&navpanes=0&view=Fit"
  width="100%"
  style="aspect-ratio: 1 / 1.294; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="paper_SmartGridComm24_An_Application_to_HV_Insulators.pdf">Download PDF</a>.
  </p>
</iframe>

---
