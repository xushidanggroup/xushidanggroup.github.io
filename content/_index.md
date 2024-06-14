---
title: Gallery
date: 2024-6-1

type: landing

sections:
  - block: slider
    content:
      slides:
      - title: Undergraduate graduation project defense
        content: 2024.5.30
        align: center
        background:
          image:
            filename: bs.jpg
            filters:
              brightness: 0.7
          position: center
          color: '#666'
      - title: Shimen Camping
        content: 2024.1.7
        align: center
        background:
          image:
            filename: sm.jpg
            filters:
              brightness: 0.7
          position: center
          color: '#666'
      - title: Winter Solstice
        content: 2023.12.22
        align: center
        background:
          image:
            filename: dz.jpg
            filters:
              brightness: 0.7
          position: center
          color: '#666'
      - title: Rafting
        content: 2023.7.25
        align: center
        background:
          image:
            filename: rafting1.jpg
            filters:
              brightness: 0.7
          position: center
          color: '#666'
    design:
      slide_height: '600px'  # 调整幻灯片高度
      is_fullscreen: false  # 不全屏显示
      loop: false
      interval: 2000
---

<style>
.slider .slide {
  display: flex;
  flex-direction: column;
  justify-content: flex-end; /* 将内容放在幻灯片底部 */
  align-items: center;
  width: 100%;
  height: 100%; /* 高度设为父容器的100% */
  background-size: contain; /* 确保背景图片完全显示 */
  background-position: center;
  padding: 20px; /* 增加内边距 */
  box-sizing: border-box; /* 包括内边距和边框 */
}

.slider .slide-title, .slider .slide-content {
  background-color: rgba(0, 0, 0, 0.5); /* 半透明背景 */
  color: #fff; /* 文字颜色 */
  padding: 10px;
  width: 100%;
  text-align: center;
  margin: 0; /* 移除默认外边距 */
}
</style>
