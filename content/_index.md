---
# Leave the homepage title empty to use the site title
title:
date: 2024-6-1
type: landing

sections:
  - block: hero
    content:
      title: |
        D
        Research Group
      image:
        filename: welcome.jpg
      text: |
        <br>
        
        The **D Research Group** has been a center of excellence for Artificial Intelligence research, teaching, and practice since its founding in 2022.
  
  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: look.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen

  - block: collection
    content:
      title: Latest Preprints
      text: ""
      count: 5
      filters:
        folders:
          - publication
        publication_type: 'article'
    design:
      view: citation
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Meet the team →" %}}
    design:
      columns: '1'
---
