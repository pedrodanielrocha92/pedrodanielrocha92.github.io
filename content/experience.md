---
title: 'Experience'
date: 2023-10-24
type: landing

design:
  spacing: '5rem'

# Note: `username` refers to the user's folder name in `content/authors/`

# Page sections
sections:
  - block: resume-experience
    content:
      username: me
    design:
      background:
        gradient_mesh:
          enable: true
      # Hugo date format
      date_format: 'January 2006'
      # Education or Experience section first?
      is_education_first: false
  - block: resume-skills
    content:
      title: Skills & Hobbies
      username: me
  - block: "tech-stack"
    design:
      style: "list"
      show_levels: true
      animations: true
    content:
      title: "Tech Stack"
      subtitle: "Technologies and tools I use across research and engineering"
      categories:

        - name: "Programming Languages"
          items:
            - name: "Python"
              icon: "devicon/python"
              level: "advanced"
            - name: "C"
              icon: "devicon/c"
              level: "advanced"
            - name: "LaTeX"
              icon: "devicon/latex"
              level: "intermediate"
            - name: "MATLAB"
              icon: "devicon/matlab"
              level: "intermediate"
            - name: "C++"
              icon: "devicon/cplusplus"
              level: "intermediate"
            - name: "Bash"
              icon: "devicon/bash"
              level: "beginner"

        - name: "Development Environments"
          items:
            - name: "Visual Studio"
              icon: "devicon/visualstudio"
              level: "beginner"
            - name: "VS Code"
              icon: "devicon/vscode"
              level: "advanced"
            - name : "Arduino IDE"
              icon: "devicon/arduino"
              level: "adavanced"
            - name: "Eclipse"
              icon: "devicon/eclipse"
              level: "beginner"
            - name: "Git"
              icon: "devicon/git"
              level: "begginer"
            - name: "Linux"
              icon: "devicon/linux"
              level: "intermediate"

        - name: "AI & Scientific Computing"
          items:
            - name: "PyTorch"
              icon: "devicon/pytorch"
              level: "beginner"
            - name: "OpenCV"
              icon: "devicon/opencv"
              level: "beginner"
            - name: "NumPy"
              icon: "devicon/numpy"
              level: "beginner"
            - name: "Pandas"
              icon: "devicon/pandas"
              level: "beginner"
            - name: "Jupyter"
              icon: "devicon/jupyter"
              level: "beginner"

        - name: "Engineering & Design"
          items:
            - name: "AutoCAD"
              icon: "brands/autocad"
              level: "intermediate"
            - name: "Fusion"
              icon: "brands/autodesk"
              level: "intermediate"
            - name: "LTspice"
              icon: "brands/ltspice"
              level: "advanced"
            - name: "Inkscape"
              icon: "devicon/inkscape"
              level: "advanced"
            - name: "GIMP"
              icon: "devicon/gimp"
              level: "intermediate"

        - name: "Research & Productivity"
          items:
            - name: "Overleaf"
              icon: "brands/overleaf"
              level: "advanced"
            - name: "Notion"
              icon: "devicon/notion"
              level: "beginner"
  - block: resume-languages
    content:
      title: Languages
      username: me

  - block: "dev-hero"
    content:
      username: "me"
      show_status: false
      show_scroll_indicator: false
---
