---
title: Contact
date: 2024-06-04

type: landing

sections:
  - block: contact
    content:
      title: Contact
      text: |-
        Welcome to join our research group
      email: test@example.org
      phone: 888 888 88 88
      address:
        street: No. 777, Xingye Avenue
        city: Guangzhou
        region: 
        postcode: '510006'
        country: China
        country_code: CN
      coordinates:
        latitude: 'x'
        longitude: 'y'
      directions: Enter Building C1 and take the stairs to Office 508 on Floor 5
      office_hours:
        - 'Monday 10:00 to 13:00'
        - 'Wednesday 09:00 to 10:00'
      appointment_url: 'https://calendly.com/xushidang'
      #contact_links:
      #  - icon: comments
      #    icon_pack: fas
      #    name: Discuss on Forum
      #    link: 'https://discourse.gohugo.io'
    
      # Automatically link email and phone or display as text?
      autolink: true
    
      # Email form provider
      form:
        provider: netlify
        formspree:
          id:
        netlify:
          # Enable CAPTCHA challenge to reduce spam?
          captcha: false
    design:
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: contact.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen
---
