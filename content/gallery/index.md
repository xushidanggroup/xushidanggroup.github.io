---
title: Gallery
date: 2024-6-1

type: landing

sections:
  - block: custom
    content:
      html: |
        <div class="gallery">
          <div class="gallery-item">
            <img src="/images/cca.jpg" alt="Image 1">
            <div class="caption">Mitochondria-targeting AIE photosensitizer is specifically synthesized inside cancer cells, realizing precise photodynamic therapy</div>
          </div>
          <div class="gallery-item">
            <img src="/images/psr.jpg" alt="Image 2">
            <div class="caption">The first lipid droplet (LD)/nucleus dual-targeted ratiometric fluorescence probe, CQPP, for monitoring polarity change was developed.</div>
          </div>
          <div class="gallery-item">
            <img src="/images/r.jpg" alt="Image 3">
            <div class="caption">The design principles of AIE PSs and their biomedical applications are discussed in detail.</div>
          </div>
        </div>
    design:
      custom_css: |
        .gallery {
          display: grid;
          grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
          gap: 16px;
          padding: 16px;
        }
        .gallery-item {
          position: relative;
          overflow: hidden;
        }
        .gallery-item img {
          width: 100%;
          height: auto;
          display: block;
        }
        .caption {
          padding: 8px;
          text-align: center;
          background: #f0f0f0;
          color: #333;
        }
---
