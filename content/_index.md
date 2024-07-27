---
# Leave the homepage title empty to use the site title
title: ""
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ""
    design:
      css_class: dark
      background:
        color: black
        image:
          # Add your image background to `assets/media/`.
          filename: simple.svg
          filters:
            brightness: 1.0
          size: cover
          position: center
          parallax: false
  - block: markdown
    content:
      id: research
      text: |-
        <a name="research"></a>
        <div style="text-align: center;">
          <h2>📚 My Research</h2>
        </div>

        My research focuses on optimal transport problems and their link with subfields of optimization, such as stochastic, online, and convex optimization. The goal is to design efficient algorithms with the best computational and statistical complexity.
    design:
      columns: '1'
  - block: collection
    content:
      title: Recent Publications/Preprints
      id: papers
      text: ""
      filters:
        folders:
          - publication
        exclude_featured: false
    design:
      view: citation
---

