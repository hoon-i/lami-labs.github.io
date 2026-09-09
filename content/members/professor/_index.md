---
title: Professor
date: 2024-01-01
type: landing

design:
  spacing: "6rem"

sections:
  - block: markdown
    id: pi
    content:
      title: Professor
      text: |
        <div class="members-section-divider"></div>
        {{< members-pi >}}
    design:
      spacing:
        padding: ["2rem", 0, "2rem", 0]
      css_style: "max-width: 100% !important; width: 100% !important;"
      container: false
  - block: markdown
    id: pi-profile
    content:
      title: ""
      text: |
        <style>
          .pi-profile { max-width: 1000px; margin: 0 auto; padding: 0 1rem; color: #374151; }
          .dark .pi-profile { color: #e2e8f0; }
          .pi-profile h3 { font-size: 1.2rem; font-weight: 700; margin: 1.75rem 0 0.6rem; color: #111827; border-bottom: 2px solid #3b82f6; padding-bottom: 0.35rem; }
          .dark .pi-profile h3 { color: #f1f5f9; }
          .pi-profile p, .pi-profile li { line-height: 1.75; }
          .pi-profile ul { padding-left: 1.25rem; margin: 0; }
        </style>
        <div class="pi-profile">
          <p>Jisoo Mok is an Assistant Professor in the Department of Electronic Engineering at Hanyang University, where she leads the Language-driven Multimodal Intelligence Lab. She previously held an assistant professor position at DGIST, and collaborated with Google Research, Amazon, and NAVER AI Lab during her doctoral studies.</p>
          <h3>Education</h3>
          <ul>
            <li>M.S./Ph.D. in Electrical and Computer Engineering, Seoul National University (Advisor: Prof. Sungroh Yoon)</li>
            <li>B.S. in Electrical Engineering, California Institute of Technology (Caltech)</li>
          </ul>
          <h3>Experience</h3>
          <ul>
            <li>2026 – present: Assistant Professor, Hanyang University</li>
            <li>2025 – 2026: Assistant Professor, DGIST</li>
            <li>2023: Research Intern, Google Research</li>
            <li>2022 – 2023: Applied Scientist Intern, Amazon Alexa AI</li>
            <li>2021: Research Intern, NAVER AI Lab</li>
          </ul>
          <h3>Academic Service</h3>
          <ul>
            <li>Reviewer: NeurIPS, ICML, ICLR, AISTATS, ACL, EMNLP, NAACL, COLING, CVPR, ICCV</li>
          </ul>
        </div>
    design:
      spacing:
        padding: ["0", 0, "2rem", 0]
  - block: markdown
    id: postdoc
    content:
      title: Post Doc
      text: |
        <div class="members-section-divider"></div>
        {{< members-postdoc >}}
    design:
      spacing:
        padding: ["2rem", 0, "2rem", 0]
      css_style: "max-width: 100% !important; width: 100% !important;"
      container: false
---
