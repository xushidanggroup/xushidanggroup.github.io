---
title: "Gallery"
date: 2023-06-19T12:00:00Z
---

<div class="gallery">
    <div class="gallery-main">
        <img src="/images/dz.jpg" alt="Main Image" id="mainImage">
        <p id="mainImageDescription">Description for dz</p>
    </div>
    <div class="gallery-thumbnails">
        <div class="thumbnail-container" onclick="showImage('/images/dz.jpg', 'Description for dz')">
            <img src="/images/dz.jpg" alt="Thumbnail dz">
            <p>Celebrate the Winter Solstice  Dec 22, 2023</p>
        </div>
        <div class="thumbnail-container" onclick="showImage('/images/f1.jpg', 'Description for f1')">
            <img src="/images/f1.jpg" alt="Thumbnail f1">
            <p>Camping trip at Shimen  Jan 7, 2024</p>
        </div>
        <div class="thumbnail-container" onclick="showImage('/images/rafting1.jpg', 'Description for rafting1')">
            <img src="/images/rafting1.jpg" alt="Thumbnail rafting1">
            <p>First team-building activity, white-water rafting  Jul 25, 2023</p>
        </div>
        <div class="thumbnail-container" onclick="showImage('/images/sm.jpg', 'Description for sm')">
            <img src="/images/sm.jpg" alt="Thumbnail sm">
            <p>Camping trip at Shimen  Jan 7, 2024</p>
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
        width: 80%;
        margin-bottom: 10px;
        text-align: center;
    }

    .gallery-main img {
        width: 100%;
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .gallery-main p {
        margin-top: 10px;
        font-size: 1em;
        color: #555;
    }

    .gallery-thumbnails {
        display: flex;
        justify-content: center;
        gap: 10px;
        overflow-x: auto;
        width: 80%;
    }

    .thumbnail-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        cursor: pointer;
    }

    .thumbnail-container img {
        width: 100px;
        height: 75px;
        transition: transform 0.3s;
    }

    .thumbnail-container img:hover {
        transform: scale(1.1);
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .thumbnail-container p {
        margin-top: 5px;
        font-size: 0.8em;
        color: #777;
        text-align: center;
    }
</style>
