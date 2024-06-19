---
title: Gallery
date: 2023-06-19T12:00:00Z
---

<style>
    h1 {
        text-align: center;
    }
</style>

<div class="gallery">
    <div class="gallery-thumbnails">
        <div class="thumbnail-container" onclick="showImage(0)">
            <img src="/images/dz.jpg" alt="Thumbnail dz">
        </div>
        <div class="thumbnail-container" onclick="showImage(1)">
            <img src="/images/f1.jpg" alt="Thumbnail f1">
        </div>
        <div class="thumbnail-container" onclick="showImage(2)">
            <img src="/images/rafting1.jpg" alt="Thumbnail rafting1">
        </div>
        <div class="thumbnail-container" onclick="showImage(3)">
            <img src="/images/sm.jpg" alt="Thumbnail sm">
        </div>
    </div>
    <p id="mainImageDescription">Celebrate the Winter Solstice  Dec 22, 2023</p>
    <div class="gallery-main">
        <button class="gallery-nav left" onclick="showPreviousImage()">&#10094;</button>
        <img src="/images/dz.jpg" alt="Main Image" id="mainImage">
        <button class="gallery-nav right" onclick="showNextImage()">&#10095;</button>
    </div>
</div>

<script>
    const images = [
        {
            src: '/images/dz.jpg',
            description: 'Celebrate the Winter Solstice  Dec 22, 2023'
        },
        {
            src: '/images/f1.jpg',
            description: 'Camping trip at Shimen  Jan 7, 2024'
        },
        {
            src: '/images/rafting1.jpg',
            description: 'First team-building activity, white-water rafting  Jul 25, 2023'
        },
        {
            src: '/images/sm.jpg',
            description: 'Camping trip at Shimen  Jan 7, 2024'
        }
    ];

    let currentIndex = 0;
    let autoSwitchInterval;

    function showImage(index) {
        currentIndex = index;
        const mainImage = document.getElementById('mainImage');
        const mainImageDescription = document.getElementById('mainImageDescription');

        // 淡出效果
        mainImage.style.opacity = 0;
        mainImageDescription.style.opacity = 0;

        setTimeout(() => {
            mainImage.src = images[index].src;
            mainImageDescription.textContent = images[index].description;

            // 淡入效果
            mainImage.style.opacity = 1;
            mainImageDescription.style.opacity = 1;
        }, 1000); // 与CSS过渡时间匹配

        resetAutoSwitch();
    }

    function showNextImage() {
        currentIndex = (currentIndex + 1) % images.length;
        showImage(currentIndex);
    }

    function showPreviousImage() {
        currentIndex = (currentIndex - 1 + images.length) % images.length;
        showImage(currentIndex);
    }

    function autoSwitchImages() {
        autoSwitchInterval = setInterval(showNextImage, 5000); // 将间隔时间改为5000毫秒（5秒）
    }

    function resetAutoSwitch() {
        clearInterval(autoSwitchInterval);
        autoSwitchImages();
    }

    document.addEventListener('DOMContentLoaded', () => {
        autoSwitchImages();
    });
</script>

<style>
    .gallery {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 20px;
    }

    .gallery-thumbnails {
        display: flex;
        justify-content: center;
        gap: 20px; /* 增加缩略图之间的间距 */
        overflow-x: auto;
        width: 95%; /* 增加缩略图显示区域的宽度 */
        margin-bottom: 10px; /* 增加缩略图和描述之间的间距 */
    }

    .thumbnail-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        cursor: pointer;
    }

    .thumbnail-container img {
        width: 150px; /* 增加缩略图的宽度 */
        height: 110px; /* 增加缩略图的高度 */
        transition: transform 0.3s;
    }

    .thumbnail-container img:hover {
        transform: scale(1.1);
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .thumbnail-container p {
        margin-top: 10px; /* 增加描述和缩略图之间的间距 */
        font-size: 0.9em; /* 增加描述文本的大小 */
        color: #777;
        text-align: center;
    }

    .gallery-main {
        width: 95%; /* 增加主图显示区域的宽度 */
        text-align: center;
        position: relative; /* 使左右按钮相对定位 */
    }

    .gallery-main img {
        width: 100%;
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
        transition: opacity 1s ease-in-out; /* 将过渡效果时间增加到1秒 */
        opacity: 1;
    }

    #mainImageDescription {
        margin-top: 10px; /* 增加描述和缩略图之间的间距 */
        margin-bottom: 10px; /* 增加描述和主图之间的间距 */
        font-size: 1.2em; /* 增加描述文本的大小 */
        color: #555;
        transition: opacity 1s ease-in-out; /* 将过渡效果时间增加到1秒 */
        opacity: 1;
    }

    .gallery-nav {
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

    .gallery-nav.left {
        left: 0;
    }

    .gallery-nav.right {
        right: 0;
    }
</style>
