---
title:
date: 2024-6-14
type: landing

sections:
  - block: markdown
    content:
      title:
      subtitle:
      text: |
        <div id="post-slider" class="post-slider">
          {{% range first 5 .Site.RegularPages.ByDate.Reverse %}}
          <div class="slide">
            <h2>{{ .Title }}</h2>
            <p>{{ .Summary }}</p>
            <a href="{{ .RelPermalink }}">Read more</a>
          </div>
          {{% end %}}
        </div>

        <style>
        .post-slider {
          width: 80%;
          margin: 0 auto;
          overflow: hidden;
          position: relative;
        }
        .slide {
          display: none;
          padding: 20px;
          background: #fff;
          border: 1px solid #ddd;
          box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .slide.active {
          display: block;
        }
        </style>

        <script>
        document.addEventListener('DOMContentLoaded', function() {
          let slides = document.querySelectorAll('.slide');
          let currentSlide = 0;
          
          function showSlide(index) {
            slides.forEach((slide, i) => {
              slide.classList.toggle('active', i === index);
            });
          }

          function nextSlide() {
            currentSlide = (currentSlide + 1) % slides.length;
            showSlide(currentSlide);
          }

          showSlide(currentSlide);
          setInterval(nextSlide, 5000); // Change slide every 5 seconds
        });
        </script>
    design:
      columns: '1'
---
