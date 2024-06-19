---
title: "Gallery"
date: 2023-06-19T12:00:00Z
---

<div class="gallery">
    <div class="gallery-main">
        <img src="/images/dz.jpg" alt="Main Image" id="mainImage">
        <p id="mainImageDescription">Celebrate the Winter Solstice  Dec 22, 2023</p>
    </div>
    <div class="gallery-thumbnails">
        <div class="thumbnail-container" onclick="showImage('/images/dz.jpg', 'Celebrate the Winter Solstice  Dec 22, 2023')">
            <img src="/images/dz.jpg" alt="Thumbnail dz">
        </div>
        <div class="thumbnail-container" onclick="showImage('/images/f1.jpg', 'Camping trip at Shimen  Jan 7, 2024')">
            <img src="/images/f1.jpg" alt="Thumbnail f1">
        </div>
        <div class="thumbnail-container" onclick="showImage('/images/rafting1.jpg', 'First team-building activity, white-water rafting  Jul 25, 2023')">
            <img src="/images/rafting1.jpg" alt="Thumbnail rafting1">
        </div>
        <div class="thumbnail-container" onclick="showImage('/images/sm.jpg', 'Camping trip at Shimen  Jan 7, 2024')">
            <img src="/images/sm.jpg" alt="Thumbnail sm">
        </div>
    </div>
</div>

<script>
    function showImage(src, description) {
        document.getElementById('mainImage').src = src;
        document.getElementById('mainImageDescription').textContent = description;
    }
</script>

<style>
    .gallery {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 20px;
    }

    .gallery-main {
        width: 95%; /* 增加主图显示区域的宽度 */
        margin-bottom: 20px; /* 增加间距 */
        text-align: center;
    }

    .gallery-main img {
        width: 100%;
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .gallery-main p {
        margin-top: 15px; /* 增加描述和图片之间的间距 */
        font-size: 1.2em; /* 增加描述文本的大小 */
        color: #555;
    }

    .gallery-thumbnails {
        display: flex;
        justify-content: center;
        gap: 20px; /* 增加缩略图之间的间距 */
        overflow-x: auto;
        width: 95%; /* 增加缩略图显示区域的宽度 */
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
</style>
