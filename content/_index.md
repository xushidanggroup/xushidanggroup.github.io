---
title:
date: 2024-06-19

type: slider

sections:
  - block: slider
    content:
      slides:
        - title: ''
          content: Mitochondria-targeting AIE photosensitizer is specifically synthesized inside cancer cells, realizing precise photodynamic therapy
          align: center
          background:
            image:
              filename: cca.jpg
              filters:
                brightness: 0.7
            position: center
            color: '#666'
        - title: ''
          content: The first lipid droplet (LD)/nucleus dual-targeted ratiometric fluorescence probe, CQPP, for monitoring polarity change was developed.
          align: center
          background:
            image:
              filename: psr.jpg
              filters:
                brightness: 0.5
            position: center
            color: '#666'
        - title: ''
          content: The design principles of AIE PSs and their biomedical applications are discussed in detail.
          align: center
          background:
            image:
              filename: r.jpg
              filters:
                brightness: 0.7
            position: center
            color: '#666'
    design:
      slide_height: '100vh'  # 设置幻灯片高度为视口高度
      is_fullscreen: true     # 设置为全屏幻灯片
      loop: false
      interval: 5000
      custom_css: |
        .slider {
          position: relative;
          height: 100vh;  /* 使用视口高度作为幻灯片容器高度 */
          overflow: hidden;  /* 隐藏溢出部分，确保只显示一个幻灯片 */
        }
        .slide {
          width: 100%;
          height: 100%;
          display: flex;
          justify-content: center;
          align-items: center;
        }
        .slide img {
          width: 100%;
          height: 100%;
          object-fit: cover;  /* 使用cover方式填充图片，确保图片铺满整个幻灯片 */
        }
---