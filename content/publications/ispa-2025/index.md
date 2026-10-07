---
title: "Automating Electrical Grid Asset Inspections Using Deep Vision: Evaluating the Impact of Annotation Detail Level"
authors:
  - me
  - Luís Cruz
  - André Coelho
  - Fernando Lopes

author_notes:
  - ""
date: 2025-10-29
publishDate: 2025-10-31
publication_types:
  - paper-conference
publication:
  name: 2025 14th International Symposium on Image and Signal Processing and Analysis
  short_name: ISPA 2025
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
  Automating visual inspections improves efficiency and consistency by addressing the limitations of manual checks, which require skilled labor and are prone to errors due to fatigue and cognitive bias. Deep learning models have enhanced computer vision generalization capabilities, being robust to label noise with large datasets. However, clean labels yield better performance than noisy ones. This study analyzes the impact of annotation detail and quality on model performance, fine-tuning several YOLOv11 models in a data-centric approach on a high-resolution HV insulator image set. Quality is evaluated along three vectors: annotation consistency (mitigating noise with strict labeling); spatial granularity (large box, small box, and polygon); and categorical definition (varying the number of annotated classes). Experimental results demonstrate improved test accuracy through enhanced label precision, and show that higher data quality reduces the need for large quantities of annotated data.
summary: Evaluating how annotation consistency, spatial granularity, and categorical definition affect HV insulator defect detection with YOLOv11.
tags:
  - Asset inspection
  - HV insulator
  - Deep vision
  - Data-centric AI
  - Label noise
featured: true
hugoblox:
  ids:
    # arxiv: ""
    doi: 10.1109/ISPA66905.2025.11259463
links:
  - type: pdf
    url: paper_ISPA_2025_Annotations_Impact_Pedro_Daniel_Rocha.pdf
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
  caption: "Evaluating the impact of annotation detail level on HV insulator defect detection."
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
  Overview of the annotation detail levels evaluated for HV insulator defect detection.
  </figcaption>
</figure>

Data-centric study on the impact of annotation quality and detail level on deep vision performance for automated electrical grid asset inspection. Several pre-trained YOLOv11 variants (small, medium, large) are fine-tuned on the Insulator Defect Image Dataset (IDID), varying labeling strategy, cross-validation fold, and model complexity (108 trained models in total).

### Background

- Manual visual inspections are labor-intensive and prone to fatigue and cognitive bias
- Deep neural networks are robust to label noise at scale, but clean labels still train better models
- Recent work focuses on model-centric improvements, underestimating the role of data quality
- In industries with limited datasets, shifting from big data to high-quality data is critical

### Challenges

- High-quality, consistently labeled data is scarce for electrical grid inspection
- Implicit or inconsistent labeling rules limit model learning potential
- Bounding-box shape and class-set choices change training signal without systematic evaluation
- High validation scores can overstate operational effectiveness on rare defect classes

### Approach

- Annotation consistency: basic vs reference vs careful quality-control policies
- Spatial granularity: large bounding box (`boxL`) vs small bounding box (`boxS`) vs polygon
- Categorical definition: 4 classes (string, good, broken, flash) vs 3 classes vs 2 defective classes only
- Cross-validation over 4 folds (400 unique images ordered by file size) and 3 YOLOv11 sizes

<!-- TODO: drop your file in as approach.png -->
<figure>
  <img src="approach.png" alt="Annotation strategies compared. " width="100%">
  <figcaption>
  Annotation strategies compared across consistency, spatial granularity, and categorical definition.
  </figcaption>
</figure>

### Data

- **Dataset**
  - Insulator Defect Image Dataset (IDID): 400 unique images (1,600 with offline mirroring)
  - Classes: String Insulator, Good Disc, Broken Disc, Flashover Shell
  - High-resolution, close-up views of real operational environments

- **Evaluation**
  - Separate test set of 88 images, annotated by the authors with a careful QC policy
  - Primary metric: Average Precision at IoU = 50% (AP50), focused on defective classes
  - Validation mAP50 of 94.8% (YOLO11-large, 4 classes) drops to 78.1% on the defective-only test set

<!-- TODO: drop your file in as data.png -->
<figure>
  <img src="data.png" alt="Dataset and evaluation setup. " width="100%">
  <figcaption>
  Dataset and evaluation setup for the IDID annotation experiments.
  </figcaption>
</figure>

### Results

- Annotation consistency: careful labeling achieves high recall and the best AP50 (flash AP50 = 82.82%); reference labeling underperforms on broken (AP50 = 49.3%) with fewer instances
- Spatial granularity: performance increases as label boundaries align more closely with defective visual features; polygons degrade less at higher IoU thresholds than boxes
- Categorical definition: no significant trend from adding functional asset classes; annotated functional assets do not necessarily improve defect detection

<!-- TODO: drop your file in as results.png -->
<figure>
  <img src="results.png" alt="Detection performance. " width="100%">
  <figcaption>
  Detection performance across annotation consistency, spatial granularity, and categorical definition.
  </figcaption>
</figure>

### Findings

- Overlooking annotation procedures and mislabeled data limits model learning potential
- Tighter spatial supervision improves precision and gradient quality
- Including frequent non-defective classes inflates development scores without improving inspection-relevant performance
- Rigorous testing on similar yet distinct data, aligned with inspection objectives, is essential

---

## Conference Paper

<iframe 
  src="paper_ISPA_2025_Annotations_Impact_Pedro_Daniel_Rocha.pdf#toolbar=0&view=Fit&navpanes=0" 
  width="100%" 
  style="aspect-ratio: 1 / 1.294; border: none;">
  <p>This browser does not support PDFs. Please download the PDF to view it: 
    <a href="paper_ISPA_2025_Annotations_Impact_Pedro_Daniel_Rocha.pdf">Download PDF</a>.
  </p>
</iframe>

---
