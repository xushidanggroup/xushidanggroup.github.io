---
title: Home
date: 2024-6-20
---

<style>
    h1 {
        text-align: center;
    }

    .homepage {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 20px;
    }

    .homepage-main {
        width: 100%; /* 利用父容器的宽度 */
        max-width: 1200px; /* 设置最大宽度 */
        text-align: center;
        position: relative;
        margin: 0 auto; /* 水平居中 */
    }

    .homepage-main img {
        max-width: 100%; /* 图片最大宽度为100%，以免在小屏幕上拉伸过大 */
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
        transition: opacity 2s ease-in-out; /* 过渡效果时间 */
        opacity: 1;
    }

    #mainImageDescription {
        margin-top: 10px; /* 增加描述和缩略图之间的间距 */
        margin-bottom: 10px; /* 增加描述和主图之间的间距 */
        font-size: 1.2em; /* 增加描述文本的大小 */
        color: #555;
        transition: opacity 2s ease-in-out; /* 将过渡效果时间增加到2秒 */
        opacity: 1;
    }

    .homepage-nav {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        font-size: 2em;
        padding: 10px;
        cursor: pointer;
        z-index: 1;
    }

    .homepage-nav.left {
        left: 0;
    }

    .homepage-nav.right {
        right: 0;
    }
</style>

<div class="homepage">
    <p id="mainImageDescription">Mitochondria-targeting AIE photosensitizer is specifically synthesized inside cancer cells, realizing precise photodynamic therapy</p>
    <div class="homepage-main">
        <button class="homepage-nav left" onclick="showPreviousImage()">&#10094;</button>
        <img src="/static/images/cca.jpg" alt="Main Image" id="mainImage">
        <button class="homepage-nav right" onclick="showNextImage()">&#10095;</button>
    </div>
</div>

<script>
    const images = [
        {
            src: '/static/images/cca.jpg',
            description: 'Mitochondria-targeting AIE photosensitizer is specifically synthesized inside cancer cells, realizing precise photodynamic therapy'
        },
        {
            src: '/static/images/psr.jpg',
            description: 'The first lipid droplet (LD)/nucleus dual-targeted ratiometric fluorescence probe, CQPP, for monitoring polarity change was developed.'
        },
        {
            src: '/static/images/r.jpg',
            description: 'The design principles of AIE PSs and their biomedical applications are discussed in detail.'
        }
    ];

    let currentIndex = 0;
    let autoSwitchInterval;
    const transitionTime = 2000; // 2秒
    const quickTransitionTime = 500; // 0.5秒

    function showImage(index, quick = false) {
        currentIndex = index;
        const mainImage = document.getElementById('mainImage');
        const mainImageDescription = document.getElementById('mainImageDescription');

        if (quick) {
            mainImage.style.transition = `opacity ${quickTransitionTime}ms ease-in-out`;
            mainImageDescription.style.transition = `opacity ${quickTransitionTime}ms ease-in-out`;
        } else {
            mainImage.style.transition = `opacity ${transitionTime}ms ease-in-out`;
            mainImageDescription.style.transition = `opacity ${transitionTime}ms ease-in-out`;
        }

        // 淡出效果
        mainImage.style.opacity = 0;
        mainImageDescription.style.opacity = 0;

        setTimeout(() => {
            mainImage.src = images[index].src;
            mainImageDescription.textContent = images[index].description;

            // 淡入效果
            mainImage.style.opacity = 1;
            mainImageDescription.style.opacity = 1;
        }, quick ? quickTransitionTime : transitionTime);

        resetAutoSwitch();
    }

    function showNextImage() {
        currentIndex = (currentIndex + 1) % images.length;
        showImage(currentIndex, true);
    }

    function showPreviousImage() {
        currentIndex = (currentIndex - 1 + images.length) % images.length;
        showImage(currentIndex, true);
    }

    function autoSwitchImages() {
        autoSwitchInterval = setInterval(showNextImage, 5000); // 将间隔时间改为5000毫秒（5秒）
    }

    function resetAutoSwitch() {
        clearInterval(autoSwitchInterval);
        autoSwitchImages();
    }

    document.addEventListener('DOMContentLoaded', () => {
        console.log('DOMContentLoaded event fired');
        autoSwitchImages();
    });
</script>
