---
title: Gallery
date: 2023-06-19T12:00:00Z
---

<style>
    h1 {
        text-align: center;
        margin-bottom: 2px;
    }

    .gallery {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 3px;
    }

    .gallery-thumbnails {
        display: flex;
        justify-content: flex-start;
        gap: 10px;
        overflow-x: auto;
        white-space: nowrap;
        width: 100%;
        margin-bottom: 2px;
        padding: 5px;
    }

    .thumbnail-container {
        display: inline-flex;
        flex-direction: column;
        align-items: center;
        cursor: pointer;
    }

    .thumbnail-container img {
        width: 130px;
        height: 90px;
        transition: transform 0.3s;
    }

    .thumbnail-container img:hover {
        transform: scale(1.1);
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .thumbnail-container p {
        margin-top: 2px;
        font-size: 0.9em;
        color: #777;
        text-align: center;
    }

    .gallery-main {
        width: 100%;
        max-width: 90vw;
        text-align: center;
        position: relative;
        margin: 0 auto;
    }

    .gallery-main img {
        max-width: 100%;
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
        transition: opacity 2s ease-in-out;
        opacity: 1;
    }

    .gallery-main .image-description {
        margin-top: 2px;
        font-size: 1em;
        color: #555;
        transition: opacity 2s ease-in-out;
        opacity: 1;
        position: absolute;
        bottom: 0;
        width: 100%;
        background-color: rgba(255, 255, 255, 0.8);
        padding: 10px;
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

    .gallery-thumbnails::-webkit-scrollbar {
        height: 8px;
    }

    .gallery-thumbnails::-webkit-scrollbar-thumb {
        background: #888;
        border-radius: 4px;
    }

    .gallery-thumbnails::-webkit-scrollbar-thumb:hover {
        background: #555;
    }

    .gallery-thumbnails::-webkit-scrollbar-track {
        background: #f1f1f1;
    }
</style>

<div class="gallery">
    <div class="gallery-thumbnails">
        <div class="thumbnail-container" onclick="showImage(0, true)">
            <img src="/images/Qingyuan rafting.jpg" alt="Thumbnail Qingyuan rafting">
        </div>
        <div class="thumbnail-container" onclick="showImage(1, true)">
            <img src="/images/dz.jpg" alt="Thumbnail dz">
        </div>
        <div class="thumbnail-container" onclick="showImage(2, true)">
            <img src="/images/sm.jpg" alt="Thumbnail sm">
        </div>
        <div class="thumbnail-container" onclick="showImage(3, true)">
            <img src="/images/Shimen 1.jpg" alt="Thumbnail Shimen 1">
        </div>
        <div class="thumbnail-container" onclick="showImage(4, true)">
            <img src="/images/Shimen 2.jpg" alt="Thumbnail Shimen 2">
        </div>
        <div class="thumbnail-container" onclick="showImage(5, true)">
            <img src="/images/Honglinhuahai.jpg" alt="Thumbnail Honglinhuahai">
        </div>
        <div class="thumbnail-container" onclick="showImage(6, true)">
            <img src="/images/羽毛球赛.jpg" alt="Thumbnail 羽毛球赛">
        </div>
        <div class="thumbnail-container" onclick="showImage(7, true)">
            <img src="/images/课题组合照.jpg" alt="Thumbnail 课题组合照">
        </div>
        <div class="thumbnail-container" onclick="showImage(8, true)">
            <img src="/images/毕业典礼合照.jpg" alt="Thumbnail 毕业典礼合照">
        </div>
        <div class="thumbnail-container" onclick="showImage(9, true)">
            <img src="/images/龙林毕业聚餐.jpg" alt="Thumbnail 龙林毕业聚餐">
        </div>
    </div>
    <div class="gallery-main">
        <button class="gallery-nav left" onclick="showPreviousImage()">&#10094;</button>
        <img src="/images/dz.jpg" alt="Main Image" id="mainImage">
        <div id="mainImageDescription" class="image-description">Celebrate the Winter Solstice - Dec 22, 2023</div>
        <button class="gallery-nav right" onclick="showNextImage()">&#10095;</button>
    </div>
</div>

<script>
    const images = [
        {
            src: '/images/Qingyuan rafting.jpg',
            description: 'First team-building activity, white-water rafting - Jul 25, 2023'
        },
        {
            src: '/images/dz.jpg',
            description: 'Celebrate the Winter Solstice - Dec 22, 2023'
        },
        {
            src: '/images/sm.jpg',
            description: 'Camping trip at Shimen - Jan 7, 2024'
        },
        {
            src: '/images/Shimen 1.jpg',
            description: 'Camping trip at Shimen - Jan 7, 2024'
        },
        {
            src: '/images/Shimen 2.jpg',
            description: 'Camping trip at Shimen - Jan 7, 2024'
        },
        {
            src: '/images/Honglinhuahai.jpg',
            description: 'Gathering at Honglin Flower Sea Restaurant to Welcome Niu Bo - Feb 29, 2024'
        },
        {
            src: '/images/羽毛球赛.jpg',
            description: 'Graduate student badminton friendly match - May 21, 2024'
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
        autoSwitchInterval = setInterval(showNextImage, 5000);
    }

    function resetAutoSwitch() {
        clearInterval(autoSwitchInterval);
        autoSwitchImages();
    }

    document.addEventListener('DOMContentLoaded', () => {
        autoSwitchImages();
    });
</script>
