---
title: Advances in Electrical Grid Assets Inspection - Exploring Multimodal Large Language Models
authors:
  - me
  - Fernando Lopes
  - Luís Cruz

author_notes:
  - ""
date: 2025-06-25
publishDate: 2025-07-15
publication_types:
  - paper-conference
publication:
  name: 2025 25th International Conference on Digital Signal Processing
  short_name: DSP 2025
peer_reviewed: true
open_access: false
license: IEEE Copyright
awards:
  - name: ""
    level: ""
    note: ""
funding:
  - funder: Fundaçãao para a Ciência e a Tecnologia
    grant: UID/50008/2025 – Instituto de Telecomunicações
  - funder: Fundaçãao para a Ciência e a Tecnologia
    grant: 2024.01914.BDANA
abstract: |
  Electrical grid asset inspection is crucial for ensuring infrastructure reliability, preventing failures, and optimizing maintenance strategies. Vision models are evolving towards multimodal, large-scale architectures, yet many industrial tasks require fine-tuning on proprietary data to capture nuanced features. This work explores the capabilities and limitations of multimodal large language models for electrical grid asset inspection, comparing pre-trained and fine-tuned versions of the Florence-VL model across detailed captioning, object detection, and segmentation. Ground-truth labels for caption tasks were generated with GPT-4, while insulator-defect annotations were used for region tasks. Fine-tuning improves class recognition and object localization, though captions often remain simplistic and lack domain-specific detail. Despite accurate GPT-4 captions, it lacks batch-processing capabilities, limiting scalability.
summary: Comparing pre-trained and fine-tuned Florence-VL on captioning, detection, and segmentation of HV insulator defects.
tags:
  - Multimodal large language models
  - Florence-VL
  - HV insulator
  - Object detection
  - Image segmentation
featured: true
hugoblox:
  ids:
    # arxiv: ""
    doi: 10.1109/DSP65409.2025.11075122
links:
  - type: pdf
    url: paper_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf
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
  caption: "Pre-trained vs fine-tuned Florence-VL on HV insulator defect inspection."
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
  Pre-trained vs fine-tuned Florence-VL across captioning, detection, and segmentation of insulator defects.
  </figcaption>
</figure>

Exploration of multimodal large language models for industry-specific electrical grid inspection, evaluating Florence-VL before and after LoRA fine-tuning on insulator defect imagery.

### Background

- Manual inspections are time-consuming, costly, and prone to inconsistencies
- CNNs and ViTs automated visual inspection; vision models now evolve toward multimodal architectures
- MLLMs trained on internet data perform strongly on generic tasks but miss industrial nuances
- Generic datasets (ImageNet, COCO) fail on repetitive patterns, subtle defects, and low-contrast regions

### Challenges

- Specialized defect vocabularies (rust, flashover, broken disc) are missing from pre-trained models
- Captioning, grounding, and segmentation must work on high-resolution operational imagery
- GPT-4 gives accurate captions but lacks batch processing for proprietary data at scale
- Fine-tuning must run on standard hardware with limited domain data

### Approach

- Pre-trained vs fine-tuned Florence-VL with LoRA (rank 16, ~3.9M trainable params, 1.4%)
- Caption tasks: `<CAPTION>`, `<DETAILED CAPTION>`, `<MORE DETAILED CAPTION>` (GPT-4o ground truth)
- Region tasks: `<REGION PROPOSAL>`, `<OD>`, `<DENSE REGION CAPTION>`
- Grounded tasks: phrase grounding, referring-expression segmentation, region-to-segmentation

<figure>
  <img src="annotation_count.png" alt="Annotation setup. " width="100%">
  <figcaption>
  Annotation setup for region-related tasks from the insulator defect dataset.
  </figcaption>
</figure>

### Data

- **Dataset**
  - Insulator Defect Image Dataset (IDID): 400 unique images (1,600 with mirroring)
  - Classes: String Insulator, Good Disc, Broken Disc, Flashover Shell
  - Curated version: standardized names, deduplicated splits, annotated test set, Roboflow release

- **Splits**
  - Train: 300 images, 3,211 instances
  - Validation: 100 images, 1,517 instances
  - Test: 88 images, 1,184 instances

<figure>
  <img src="data_sample.jpg" alt="Canonical dataset samples. " width="100%">
  <figcaption>
  Canonical samples of each class and class distribution across splits.
  </figcaption>
</figure>

### Results

- Fine-tuning improves class recognition and object localization; captions stay simplistic
- Object detection mAP50 of 53.6% after fine-tuning (vs 89.7% YOLOv8 and 94.8% YOLO11 benchmarks)
- Referring-expression segmentation works on blurred backgrounds even pre-trained, with errors
- Region-to-segmentation often improves after fine-tuning, with mixed per-object results

<figure>
  <img src="results.jpg" alt="Captioning and detection results. " width="100%">
  <figcaption>
  Captioning and detection results for pre-trained and fine-tuned models.
  </figcaption>
</figure>

<figure>
  <img src="results_1.jpg" alt="Segmentation results, example 1. " width="100%">
  <figcaption>
  Referring-expression and region-to-segmentation results, example 1.
  </figcaption>
</figure>

<figure>
  <img src="results_2.jpg" alt="Segmentation results, example 2. " width="100%">
  <figcaption>
  Referring-expression and region-to-segmentation results, example 2.
  </figcaption>
</figure>

### Findings

- Domain-specific fine-tuning is required for industrial defect vocabularies
- Detection and segmentation transfer better than free-form captioning
- High-quality, consistently labeled data matters more than generic scale
- Tailored caption datasets are needed to close the semantic gap

---

## Conference Paper

<iframe
  src="paper_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf#toolbar=0&view=Fit&navpanes=0"
  width="100%"
  style="aspect-ratio: 1 / 1.294; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="paper_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---
