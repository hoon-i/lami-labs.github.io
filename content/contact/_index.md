---
title: Contact
date: 2024-01-01
type: landing

design:
  spacing: "6rem"

sections:
  - block: markdown
    id: contact
    content:
      title: Contact
      text: |
        {{< contact-panel >}}
    design:
      spacing:
        padding: ["4.25rem", 0, "3rem", 0]
      css_class: "bg-white dark:bg-gray-800"

  - block: markdown
    id: resources
    content:
      title: Resources
      text: |
        {{< resource-cards >}}
    design:
      spacing:
        padding: ["2rem", 0, "3rem", 0]
      css_class: "bg-white dark:bg-gray-800"
---
