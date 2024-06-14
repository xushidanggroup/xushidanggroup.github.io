---
title: 
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
      slide_height: ''  # 留空以使用CSS来控制高度
      is_fullscreen: false  # 不全屏显示
      loop: false
      interval: 2000
---

<style>
/* 主容器，用于幻灯片 */
.slider-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

/* 幻灯片 */
.slider .slide {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 50vh; /* 高度设为视窗高度的一半 */
  margin: 0 auto;
  background-size: cover; /* 确保背景图片覆盖整个幻灯片 */
  background-position: center; /* 背景图片居中 */
}

/* 标题和内容的容器 */
.slider .slide-title, .slider .slide-content {
  background-color: rgba(0, 0, 0, 0.5); /* 半透明背景 */
  color: #fff; /* 文字颜色 */
  padding: 10px;
  width: 100%;
  text-align: center;
  box-sizing: border-box; /* 包括内边距和边框 */
  margin-top: 10px;
}

/* 标题和内容容器的父级 */
.slider .slide-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  margin-top: 20px;
}

/* 媒体查询，针对不同的视窗高度 */
@media (max-height: 600px) {
  .slider .slide {
    height: 75vh; /* 更高的视窗高度 */
  }
}

@media (min-height: 800px) {
  .slider .slide {
    height: 40vh; /* 较低的视窗高度 */
  }
}
</style>
