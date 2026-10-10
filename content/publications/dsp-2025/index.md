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
  Electrical grid asset inspection is crucial for ensuring infrastructure reliability, preventing failures, and optimizing maintenance strategies. Traditional methods rely heavily on manual labor, making inspections time-consuming, costly, and prone to inconsistencies. Recent advances in deep learning, particularly CNNs and ViTs, have shown potential for automating visual inspection tasks. Vision models are evolving towards multimodal, large-scale architectures. While MLLMs trained on diverse internet-sourced datasets show strong performance, many industrial tasks require models fine-tuned on proprietary data to capture the nuanced features necessary for specialization. This work explores the capabilities and limitations of multi-modal large language models for electrical grid asset inspection, comparing pre-trained and fine-tuned versions of the Florence-VL model across tasks like detailed captioning, object detection, and segmentation. Ground truth labels for caption-related tasks were generated using GPT-4, while annotations from a dataset of insulator defects were used for region-related tasks. Results indicate that fine-tuning improves class recognition and object localization, though captions often remain simplistic and lack domain-specific detail. Despite GPT-4 providing accurate captions, it lacks batch-processing capabilities, limiting its scalability. These findings underscore the importance of domain-specific fine-tuning and high-quality data to enhance MLLM performance.
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
  - type: slides
    url: "slides_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf"
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

> **Copyright notice:** © 2025 IEEE. Personal use of this material is permitted. Permission from IEEE must be obtained for all other uses. The published version is available via [IEEE Xplore](https://doi.org/10.1109/DSP65409.2025.11075122).

---

## Overview

Simple comparative study: pre-trained vs fine-tuned Florence-2 on HV insulator inspection, across captioning, detection, and segmentation.

### Method

- **PT:** [Florence-2-base-ft](https://huggingface.co/microsoft/Florence-2-base-ft) evaluated zero-shot.
- **FT:** the same model LoRA-fine-tuned on curated [IDID](https://doi.org/10.21227/VKDW-X769) — 300 images, 3.1k region annotations, 4 classes.
- Ground truth: GPT-4o for captions, IDID annotations for detection and segmentation.

### Data

- **IDID:** 400 unique images (1,600 with mirroring); classes: String Insulator, Good Disc, Broken Disc, Flashover Shell.
- Splits: train 300 / 3,211 instances, valid 100 / 1,517, test 88 / 1,184.

<figure>
  <img src="figures/data_sample.jpg" alt="Canonical dataset samples." width="100%">
  <img src="figures/annotation_count.png" alt="Annotation counts per class across train, validation and test splits." width="100%">
  <figcaption>
  Canonical samples of each class, with annotation counts per class across splits.
  </figcaption>
</figure>

### Results

#### Caption Tasks

- PT captions stay generic and often hallucinate off-domain objects; FT collapses to the trained class names with repetitive text.
- GPT-4o ground truth stays descriptive and domain-specific.

<figure>
  <img src="figures/caption1.jpg" alt="Detailed caption results, example 1." width="100%">
  <figcaption>
  Detailed caption, example 1: PT vs FT against GPT-4o ground truth.
  </figcaption>
</figure>

<figure>
  <img src="figures/caption2.jpg" alt="Detailed caption results, example 2." width="100%">
  <figcaption>
  Detailed caption, example 2: PT vs FT against GPT-4o ground truth.
  </figcaption>
</figure>

#### Segmentation

- Works on blurred backgrounds even pre-trained, with visible errors; fine-tuning improves masks but with mixed per-object results.

<figure>
  <img src="figures/phrase2segment_PT.jpg" alt="Phrase grounding segmentation by the pre-trained model." width="100%">
  <figcaption>
  Phrase grounding to segmentation with the pre-trained model on a free-text defect description.
  </figcaption>
</figure>

<figure>
  <img src="figures/box2segment.jpg" alt="Region-to-segmentation: labels vs PT vs FT." width="100%">
  <figcaption>
  Region-to-segmentation: ground-truth labels vs pre-trained vs fine-tuned masks.
  </figcaption>
</figure>

#### Object Detection

- Fine-tuning improves class recognition and object localization, but the model still confuses flashover with good discs.

| Work     | Model            | # Params | mAP@50 |
|----------|------------------|----------|--------|
| Ours     | Florence-2-base  | 0.23B    | 53.6%  |
| [1]      | YOLOv8s          | 11.2M    | 89.7%  |
| [2]      | YOLO11l          | 20.1M    | 94.8%  |

- [1] [SmartGridComm 2024](https://doi.org/10.1109/SmartGridComm60555.2024.10738034) — YOLOv8s on HV insulators.
- [2] [ISPA 2025](https://doi.org/10.1109/ISPA66905.2025.11259463) — YOLOv11-large on the same dataset.

Multimodal models remain well behind these specialist CNN detectors, despite comparable or larger parameter counts — a key limitation for inspection use.

<figure>
  <img src="figures/OD1.jpg" alt="Object detection: labels vs FT, example 1." width="100%">
  <figcaption>
  Detection example 1: ground-truth labels vs FT output — broken disc and surrounding good discs recovered.
  </figcaption>
</figure>

<figure>
  <img src="figures/OD2.jpg" alt="Object detection: labels vs FT, example 2." width="100%">
  <figcaption>
  Detection example 2: ground-truth labels vs FT output on a flashover string.
  </figcaption>
</figure>

### Takeaways

- Fine-tuning is required for industrial defect vocabularies, but captions remain simplistic.
- Detection and segmentation transfer better than free-form captioning.
- Specialist CNN detectors still outperform MLLMs on detection accuracy.

---

## Conference Paper

A self-archived accepted manuscript is provided below. <br>
The published version is available in [IEEE Xplore](https://doi.org/10.1109/DSP65409.2025.11075122).

<iframe
  src="paper_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf#toolbar=0&navpanes=0&view=Fit"
  width="100%"
  style="aspect-ratio: 1 / 1.294; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="paper_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---

## Conference Slides

<iframe
  src="slides_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf#toolbar=0&navpanes=0&view=Fit"
  width="100%"
  style="aspect-ratio: 4/3; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it:
    <a href="slides_DSP_2025_HV_Insulators_MLLMs_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---
