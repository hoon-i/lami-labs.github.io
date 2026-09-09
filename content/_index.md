---
title: 'Home'
date: 2023-10-24
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: hero
    content:
      title: LaMI Lab
      #title: "<span class='hero-i'>I</span>ntelligent <span class='hero-s'>S</span>ystems and <span class='hero-l'>L</span>earning Laboratory"
      text: Language-driven Multimodal Intelligence Lab
      announcement:
        text: "We are recruiting M.S./Ph.D. students and undergraduate interns."
        link:
          text: "Apply"
          url: "/join/"
    design:
      no_padding: true
      # For full-screen, add `min-h-screen` below
      css_class: "dark"
      background:
        color: "#1f2125"
        image:
          # Add your image background to `assets/media/`.
          # filename: bg-triangles.svg
          filename: home.png
          filters:
            brightness: 1.0
          size: cover
          position: center
          parallax: false
  # - block: stats
  #   content:
  #     items:
  #       - statistic: "1M+"
  #         description: |
  #           Websites built  
  #           with Hugo Blox
  #       - statistic: "10k+"
  #         description: |
  #           GitHub stars  
  #           since 2016
  #       - statistic: "3k+"
  #         description: |
  #           Discord community  
  #           for support
  #   design:
  #     # Section background color (CSS class)
  #     css_class: "bg-gray-100 dark:bg-gray-900"
  #     # Reduce spacing
  #     spacing:
  #       padding: ["1rem", 0, "1rem", 0]
  - block: markdown
    id: intro
    content:
      title: ""
      text: |
        <style>
          #intro .max-w-prose, #intro .prose { max-width: 1100px !important; width: 100% !important; }
          .lab-intro-text { color: #3b3f45; }
          .dark .lab-intro-text { color: #d9dadc; }
          .lab-intro-link { color: #1f2125; font-weight: 700; text-decoration: underline; text-underline-offset: 3px; text-decoration-thickness: 2px; }
          .lab-intro-link:hover { color: #3b3f45; }
          .dark .lab-intro-link { color: #ffffff; }
        </style>
        <div style="max-width: 1100px; margin: 0 auto;">
          <p class="lab-intro-text" style="font-size: 1.1rem; line-height: 1.85; margin: 0 0 0.6rem;">
            Welcome to the <strong>Language-driven Multimodal Intelligence Lab (LaMI Lab)</strong> at <strong>Hanyang University</strong>, led by <strong>Prof. Jisoo Mok</strong>.
            Our research group is committed to building AI agents that are practical and trustworthy.
          </p>
          <p class="lab-intro-text" style="font-size: 1.1rem; line-height: 1.85; margin: 0;">
            LaMI Lab is looking for curious, passionate, and highly motivated students (M.S./Ph.D.), as well as undergraduate interns to join our research group. <a href="/join/" class="lab-intro-link">Join us →</a>
          </p>
        </div>
    design:
      spacing:
        padding: ["3rem", 0, "1rem", 0]

  - block: markdown
    id: research-areas
    content:
      title: ""
      text: |
        <style>
          #research-areas .max-w-prose, #research-areas .prose { max-width: 1100px !important; width: 100% !important; }
          .ra-grid { display: grid; grid-template-columns: 1fr; gap: 1.25rem; max-width: 1100px; margin: 0 auto; }
          @media (min-width: 860px) { .ra-grid { grid-template-columns: repeat(3, minmax(0, 1fr)); } }
          .ra-card { background: #ffffff; border: 1px solid #d9dadc; border-radius: 1rem; padding: 1.75rem 1.6rem; box-shadow: 0 8px 20px rgba(31, 33, 37, 0.05); }
          .dark .ra-card { background: #3b3f45; border-color: #3b3f45; }
          .ra-card h3 { margin: 0 0 0.6rem; font-size: 1.15rem; font-weight: 700; color: #1f2125; }
          .dark .ra-card h3 { color: #ffffff; }
          .ra-card p { margin: 0; color: #3b3f45; line-height: 1.7; font-size: 0.98rem; }
          .dark .ra-card p { color: #d9dadc; }
        </style>
        <h2 style="text-align: center; margin-bottom: 0.5rem; font-size: 2rem; font-weight: 700;">Building Smarter, More Reliable AI Agents</h2>
        <p style="text-align: center; color: #8b9097; margin: 0 auto 2rem; max-width: 720px;">Our research group is committed to building AI agents that are practical and trustworthy.</p>
        <div class="ra-grid">
          <div class="ra-card">
            <h3>Advancing LLM Capabilities</h3>
            <p>We're pushing the boundaries of what large language models and multimodal models can do, making them fundamentally more capable and versatile, toward AI-driven scientific discovery and open-ended research.</p>
          </div>
          <div class="ra-card">
            <h3>Connecting Models to Real-World Data</h3>
            <p>We seamlessly augment the knowledge base of these models to integrate and learn from diverse real-world data, including graphs, time-series, and tables.</p>
          </div>
          <div class="ra-card">
            <h3>Trustworthy Evaluation</h3>
            <p>We explore new evaluation frameworks to ensure that these advanced AI agents are reliable and transparent.</p>
          </div>
        </div>
    design:
      spacing:
        padding: ["2rem", 0, "2rem", 0]
      css_style: "max-width: 100% !important; width: 100% !important;"
      container: false
  - block: markdown
    id: news
    content:
      title: ""
      text: |
        <h2 style="text-align: center; margin-bottom: 2rem; font-size: 2rem; font-weight: 700;">Latest News</h2>
        {{< news-cards >}}
    design:
      spacing:
        padding: ["2rem", 0, "2rem", 0]
      css_style: "max-width: 100% !important; width: 100% !important;"
      container: false
  # - block: cta-image-paragraph
  #   id: solutions
  #   content:
  #     items:
  #       - title: Build your future-proof website
  #         text: As easy as 1, 2, 3!
  #         feature_icon: check
  #         features:
  #           - "Future-proof - edit your content in text files"
  #           - "Website is generated by a single app, Hugo"
  #           - "No JavaScript knowledge required"
  #         # Upload image to `assets/media/` and reference the filename here
  #         image: build-website.png
  #         button:
  #           text: Get Started
  #           url: https://hugoblox.com/templates/
  #       - title: Large Community
  #         text: Join our large community on Discord - ask questions and get live responses
  #         feature_icon: bolt
  #         features:
  #           - "Dedicated support channel"
  #           - "3,000+ users on Discord"
  #           - "Share your site and get feedback"
  #         # Upload image to `assets/media/` and reference the filename here
  #         image: coffee.jpg
  #         button:
  #           text: Join Discord
  #           url: https://discord.gg/z8wNYzb
  #   design:
  #     # Section background color (CSS class)
  #     css_class: "bg-gray-100 dark:bg-gray-900"
  # - block: testimonials
  #   content:
  #     title: ""
  #     text: ""
  #     items:
  #       - name: "Hugo Smith"
  #         role: "Marketing Executive at X"
  #         # Upload image to `assets/media/` and reference the filename here
  #         image: "testimonial-1.jpg"
  #         text: "Awesome, so easy to use and saved me so much work with the swappable pre-designed sections!"
  #   design:
  #     spacing:
  #       # Reduce bottom spacing so the testimonial appears vertically centered between sections
  #       padding: ["6rem", 0, 0, 0]
  # - block: cta-card
  #   content:
  #     title: Build your future-proof website
  #     text: As easy as 1, 2, 3!
  #     button:
  #       text: Get Started
  #       url: https://hugoblox.com/templates/
  #   design:
  #     card:
  #       # Card background color (CSS class)
  #       css_class: "bg-primary-300"
  #       css_style: ""
---
