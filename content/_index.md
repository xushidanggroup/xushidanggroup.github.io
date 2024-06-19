---
title:
date: 2024-06-19T00:00:00Z
draft: false
---

<!-- 幻灯片展示 -->
<div id="slider" style="width: 100%; max-width: 600px; margin: auto;">
  <div class="slides">
    <img src="/images/cca.jpg" alt="Mitochondria-targeting AIE photosensitizer" style="width: 100%;">
    <div class="description">Mitochondria-targeting AIE photosensitizer is specifically synthesized inside cancer cells, realizing precise photodynamic therapy.</div>
  </div>
  <div class="slides">
    <img src="/images/psr.jpg" alt="Lipid droplet (LD)/nucleus dual-targeted ratiometric fluorescence probe" style="width: 100%;">
    <div class="description">The first lipid droplet (LD)/nucleus dual-targeted ratiometric fluorescence probe, CQPP, for monitoring polarity change was developed.</div>
  </div>
  <div class="slides">
    <img src="/images/r.jpg" alt="Design principles of AIE PSs" style="width: 100%;">
    <div class="description">The design principles of AIE PSs and their biomedical applications are discussed in detail.</div>
  </div>
</div>

<!-- 幻灯片样式 -->
<style>
#slider {
  position: relative;
}
.slides {
  display: none;
  text-align: center;
  position: relative;
}
.slides img {
  vertical-align: middle;
}
.description {
  position: absolute;
  bottom: 10px;
  width: 100%;
  text-align: center;
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  padding: 10px;
}
</style>

<!-- 幻灯片脚本 -->
<script>
let slideIndex = 0;
showSlides();

function showSlides() {
  let i;
  let slides = document.getElementsByClassName("slides");
  for (i = 0; i < slides.length; i++) {
    slides[i].style.display = "none";  
  }
  slideIndex++;
  if (slideIndex > slides.length) {slideIndex = 1}    
  slides[slideIndex - 1].style.display = "block";  
  setTimeout(showSlides, 3000); // 每3秒切换一次图片
}
</script>
