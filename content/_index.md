---
title: ""
summary: ""
date: "2022-10-24"
type: "landing"
sections:
  - block: "resume-biography-3"
    content:
      username: "me"
      text: ""
      button:
        text: "Download CV"
        url: "uploads/resume.pdf"
      headings:
        about: ""
        education: ""
        interests: ""
    design:
      css_style: |
        /* Lower the minmax value so two items fit side-by-side */
        .resume-biography-3 ul { 
          display: grid !important; 
          grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)) !important; 
          gap: 2rem !important;
        }
        .resume-biography-3 li { 
          min-width: 280px !important; 
          max-width: 100% !important;
        }
      background:
        gradient_mesh:
          enable: true
      name:
        size: "md"
      avatar:
        size: "large"
        shape: "circle"
    ce: "section-823b6304"
    As: "section-ae7d5c80"
  - block: "markdown"
    content:
      title: "🔬 My Research"
      subtitle: "Automating Electrical Grid Asset Inspection"
      text: |-
        My research explores how AI-based Computer Vision can enable reliable and scalable Automated Inspection of electrical infrastructure. Despite significant advances in artificial intelligence, automated inspection systems still struggle to match the capabilities of human experhhs, particularly when moving from controlled benchmarks to real operational environments.

        I investigate this gap from a system-level perspective. Rather than treating model accuracy as the sole determinant of inspection performance, my work considers how data acquisition, dataset development, annotation, model design, and validation interact with one another and with the requirements of real inspection operations. This perspective addresses practical challenges such as insufficiently representative data, inappropriate acquisition strategies, inconsistent validation practices, and the divergence between benchmark metrics and operational performance.

        I explore approaches for building inspection systems that can adapt and improve throughout their lifecycle, using active learning for continuous model improvement, leveraging efficient sensing with embedded vision for on-site data validation, and combining advanced computing with multimodal data and models to incorporate physical and domain knowledge. A central objective is to establish better alignment between sensing, computing, and operational requirements to enable the next generation of fully autonomous inspection systems.

        This work is conducted in close collaboration with industry, allowing research questions to emerge from real inspection challenges and providing a direct connection between methodological development and practical requirements. Ultimately, I aim to contribute to the development of intelligent vision systems that are not only accurate in controlled experiments, but reliable, scalable, and useful in real-world inspection.

        [![Graphical Abstract](/publications/IEEE_Access/graphical_abstract.png)](/publications/IEEE_Access/)

    design:
        
      css_class: "max-w-full mx-auto text-9xl"

    ce: "section-research"
    id: "research"
    As: "section-4f719b15"

  - block: "collection"
    content:
      title: "Featured Publications"
      filters:
        folders:
          - "publications"
        featured_only: true
    design:
      background:
        gradient_mesh:
          enable: true
      view: "article-grid"
      columns: 2
    ce: "section-papers"
    As: "section-64848e6c"
  - block: "collection"
    content:
      title: "Recent Publications"
      text: ""
      filters:
        folders:
          - "publications"
        exclude_featured: false
    design:
      view: "citation"
    ce: "section-b5ae280e"
    As: "section-879c541a"
  - block: "collection"
    content:
      title: "Recent Presentations"
      filters:
        folders:
          - "slides"
      page_type: "slides"
    design:
      background:
        gradient_mesh:
          enable: true
      view: "card"
    ce: "section-talks"
    id: "presentations"
    As: "section-7c16c238"
  - block: "collection"
    content:
      title: "Recent Events"
      subtitle: ""
      text: ""
      page_type: "events"
      count: 6
      filters:
        author: ""
        category: ""
        tag: ""
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ""
      offset: 0
      order: "desc"
      sort_by: "Date"
    design:
      view: "card"
    ce: "section-news"
    id: "events"
    As: "section-446372d1"
  - block: "dev-hero"
    content:
      username: "me"
      show_status: false
      show_scroll_indicator: false
      scroll_target: "#projects"
    ce: "section-6-dev-hero"
    As: "section-a0e18236"
---
