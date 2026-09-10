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
      title: ""
      text: |
        <style>
          #pi .max-w-prose, #pi .prose { max-width: 1100px !important; width: 100% !important; }

          .pi-hero { display: grid; grid-template-columns: 1fr; gap: 2rem; align-items: start; }
          @media (min-width: 820px) { .pi-hero { grid-template-columns: 280px minmax(0, 1fr); gap: 3rem; } }

          .pi-photo { width: 100%; max-width: 280px; aspect-ratio: 3 / 4; border-radius: 0.9rem; overflow: hidden; background: #d9dadc; box-shadow: 0 10px 24px rgba(31, 33, 37, 0.10); margin: 0 auto; }
          .dark .pi-photo { background: #3b3f45; }
          .pi-photo img { width: 100%; height: 100%; object-fit: cover; display: block; }

          .pi-name { font-size: 2rem; font-weight: 800; margin: 0 0 0.25rem; color: #1f2125; line-height: 1.2; }
          .dark .pi-name { color: #f3f4f5; }
          .pi-role { margin: 0 0 1.25rem; color: #1f2125; font-weight: 600; font-size: 1rem; }
          .dark .pi-role { color: #d9dadc; }
          .pi-intro p { margin: 0 0 0.9rem; color: #3b3f45; line-height: 1.8; font-size: 1rem; }
          .dark .pi-intro p { color: #d9dadc; }
          .pi-intro a { color: #1f2125; font-weight: 600; text-decoration: none; }
          .pi-intro a:hover { text-decoration: underline; }
          .dark .pi-intro a { color: #d9dadc; }
          .pi-links { display: flex; flex-wrap: wrap; gap: 0.6rem; margin-top: 1rem; }
          .pi-links a { display: inline-flex; align-items: center; gap: 0.4rem; padding: 0.45rem 0.9rem; border-radius: 999px; border: 1px solid #d9dadc; font-size: 0.9rem; font-weight: 600; color: #3b3f45; text-decoration: none; }
          .pi-links a:hover { border-color: #1f2125; color: #1f2125; }
          .dark .pi-links a { border-color: #8b9097; color: #d9dadc; }

          .pi-sections { display: grid; grid-template-columns: 1fr; gap: 1.5rem 3rem; margin-top: 3rem; }
          @media (min-width: 820px) { .pi-sections { grid-template-columns: 1fr 1fr; } }
          .pi-section h3 { font-size: 1.15rem; font-weight: 700; margin: 0 0 0.75rem; padding-bottom: 0.4rem; border-bottom: 2px solid #1f2125; color: #1f2125; }
          .dark .pi-section h3 { color: #ffffff; }
          .pi-section ul { list-style: none; margin: 0; padding: 0; }
          .pi-section li { padding: 0.35rem 0; color: #3b3f45; line-height: 1.6; font-size: 0.97rem; }
          .dark .pi-section li { color: #d9dadc; }
          .pi-section li span { display: inline-block; min-width: 7.5rem; margin-right: 0.5rem; color: #8b9097; font-variant-numeric: tabular-nums; }
          .dark .pi-section li span { color: #8b9097; }
        </style>

        <div class="pi-hero">
          <div class="pi-photo">
            <img src="/media/members/jisoo-mok.jpg" alt="Jisoo Mok" onerror="this.style.display='none'">
          </div>
          <div class="pi-intro">
            <h2 class="pi-name">Jisoo Mok</h2>
            <p class="pi-role">Assistant Professor · Department of Electronic Engineering, Hanyang University</p>
            <p>Jisoo Mok is an assistant professor in the Department of Electronic Engineering at Hanyang University, where she leads LaMI Lab: Language-driven Multimodal Intelligence Lab.</p>
            <p>Before joining Hanyang University, she was an assistant professor in the Department of EE&amp;CS @ DGIST. She obtained her Ph.D. degree at Seoul National University, during which she was advised by Prof. Sungroh Yoon. Before her time at Seoul National University, she received her B.S. degree from California Institute of Technology (Caltech).</p>
            <p>During her Ph.D. studies, she collaborated with researchers from domestic and global AI research labs, e.g., Google Research, Amazon, and NAVER.</p>
            <div class="pi-links">
              <a href="https://drive.google.com/file/d/1C5vFgiKYQgPLKVXFsI8teTg1PL-6XBVF/view?usp=sharing" target="_blank" rel="noopener">Curriculum Vitae</a>
              <a href="mailto:jisoomok@hanyang.ac.kr">jisoomok@hanyang.ac.kr</a>
            </div>
          </div>
        </div>

        <div class="pi-sections">
          <div class="pi-section">
            <h3>Education</h3>
            <ul>
              <li>M.S./Ph.D. in Electrical and Computer Engineering, Seoul National University, Korea</li>
              <li>B.S. in Electrical Engineering, Caltech, Pasadena, U.S.A.</li>
            </ul>
          </div>
          <div class="pi-section">
            <h3>Professional Experience</h3>
            <ul>
              <li><span>2026 – current</span>Assistant Professor, Hanyang University</li>
              <li><span>2025 – 2026</span>Assistant Professor, Daegu Gyeongbuk Institute of Science and Technology (DGIST)</li>
              <li><span>2023</span>Research Intern, Google Research</li>
              <li><span>2022, 2023</span>Applied Scientist Intern, Amazon Alexa AI</li>
              <li><span>2021</span>Research Intern, NAVER AI Lab</li>
            </ul>
          </div>
          <div class="pi-section">
            <h3>Academic Service</h3>
            <ul>
              <li>Reviewer: NeurIPS, ICML, ICLR, AISTATS, ACL, EMNLP, NAACL, COLING, CVPR, ICCV</li>
            </ul>
          </div>
          <div class="pi-section">
            <h3>Invited Talks &amp; Presentations</h3>
            <ul>
              <li><span>2025</span>LLM Lecture Series, LG Electronics CTO Department</li>
              <li><span>2022, 2023</span>SNU AI Retreat</li>
            </ul>
          </div>
        </div>
    design:
      spacing:
        padding: ["4.25rem", 0, "3rem", 0]

---
