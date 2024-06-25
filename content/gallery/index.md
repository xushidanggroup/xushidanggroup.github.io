---
title: Gallery
date: 2023-06-19T12:00:00Z
---

<style>
    h1 {
        text-align: center;
        margin-bottom: 2px; /* 减小标题下方的间距 */
    }

    .gallery {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 3px; /* 减小整个gallery的上边距 */
    }

    .gallery-thumbnails {
        display: flex;
        justify-content: flex-start; /* 使缩略图从左边开始排列 */
        gap: 10px; /* 减小缩略图之间的间距 */
        overflow-x: auto; /* 添加水平滚动条 */
        white-space: nowrap; /* 防止缩略图换行 */
        width: 100%; /* 利用更大区域来显示缩略图 */
        margin-bottom: 2px; /* 减小缩略图和描述之间的间距 */
        padding: 5px; /* 添加一些内边距以增加滚动条的可见性 */
    }

    .thumbnail-container {
        display: inline-flex; /* 使容器显示为行内块级元素 */
        flex-direction: column;
        align-items: center;
        cursor: pointer;
    }

    .thumbnail-container img {
        width: 130px; /* 调整缩略图的宽度 */
        height: 90px; /* 调整缩略图的高度 */
        transition: transform 0.3s;
    }

    .thumbnail-container img:hover {
        transform: scale(1.1);
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .thumbnail-container p {
        margin-top: 2px; /* 减小描述和缩略图之间的间距 */
        font-size: 0.9em; /* 调整描述文本的大小 */
        color: #777;
        text-align: center;
    }

    .gallery-main {
        width: 100%; /* 利用父容器的宽度 */
        max-width: 90vw; /* 设置最大宽度为视口宽度的90% */
        text-align: center;
        position: relative;
        margin: 0 auto; /* 水平居中 */
    }

    .gallery-main img {
        max-width: 100%; /* 图片最大宽度为100%，以免在小屏幕上拉伸过大 */
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
        transition: opacity 2s ease-in-out; /* 过渡效果时间 */
        opacity: 1;
    }

    #mainImageDescription {
        margin-top: 2px; /* 减小描述和缩略图之间的间距 */
        margin-bottom: 2px; /* 减小描述和主图之间的间距 */
        font-size: 1em; /* 调整描述文本的大小 */
        color: #555;
        transition: opacity 2s ease-in-out; /* 将过渡效果时间增加到2秒 */
        opacity: 1;
    }

    .gallery-nav {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        font-size: 2em; /* 调整导航按钮的大小 */
        padding: 10px; /* 增加按钮的内边距 */
        cursor: pointer;
        z-index: 1;
    }

    .gallery-nav.left {
        left: 0;
    }

    .gallery-nav.right {
        right: 0;
    }

    /* 添加滚动条样式 */
    .gallery-thumbnails::-webkit-scrollbar {
        height: 8px; /* 滚动条的高度 */
    }

    .gallery-thumbnails::-webkit-scrollbar-thumb {
        background: #888; /* 滚动条的颜色 */
        border-radius: 4px;
    }

    .gallery-thumbnails::-webkit-scrollbar-thumb:hover {
        background: #555; /* 滚动条悬停时的颜色 */
    }

    .gallery-thumbnails::-webkit-scrollbar-track {
        background: #f1f1f1; /* 滚动条轨道的颜色 */
    }
</style>

<div class="gallery">
    <div class="gallery-thumbnails">
        <div class="thumbnail-container" onclick="showImage(0, true)">
            <img src="/images/dz.jpg" alt="Thumbnail dz">
        </div>
        <div class="thumbnail-container" onclick="showImage(1, true)">
            <img src="/images/rafting1.jpg" alt="Thumbnail rafting1">
        </div>
        <div class="thumbnail-container" onclick="showImage(2, true)">
            <img src="/images/sm.jpg" alt="Thumbnail sm">
        </div>
        <div class="thumbnail-container" onclick="showImage(3, true)">
            <img src="/images/课题组合照.jpg" alt="Thumbnail 课题组合照">
        </div>
        <div class="thumbnail-container" onclick="showImage(4, true)">
            <img src="/images/毕业典礼合照.jpg" alt="Thumbnail 毕业典礼合照">
        </div>
        <div class="thumbnail-container" onclick="showImage(5, true)">
            <img src="/images/龙林毕业聚餐.jpg" alt="Thumbnail 龙林毕业聚餐">
        </div>
        <div class="thumbnail-container" onclick="showImage(6, true)">
            <img src="/images/羽毛球赛.jpg" alt="Thumbnail 羽毛球赛">
        </div>
    </div>
    <p id="mainImageDescription">Celebrate the Winter Solstice - Dec 22, 2023</p>
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
            description: 'Celebrate the Winter Solstice - Dec 22, 2023'
        },
        {
            src: '/images/rafting1.jpg',
            description: 'First team-building activity, white-water rafting - Jul 25, 2023'
        },
        {
            src: '/images/sm.jpg',
            description: 'Camping trip at Shimen - Jan 7, 2024'
        },
        {
            src: '/images/课题组合照.jpg',
            description: 'College photo day - Jun 7, 2024'
        },
        {
            src: '/images/毕业典礼合照.jpg',
            description: 'College graduation ceremony - Jun 18, 2024'
        },
        {
            src: '/images/龙林毕业聚餐.jpg',
            description: 'Undergraduate graduation dinner - Jun 19, 2024'
        },
        {
            src: '/images/羽毛球赛.jpg',
            description: 'Graduate student badminton friendly match - May 21, 2024'
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
        autoSwitchImages();
    });
</script>
