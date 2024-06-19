---
title: "Gallery"
date: 2023-06-19T12:00:00Z
---

<div class="gallery">
    <div class="gallery-main">
        <img src="/images/dz.jpg" alt="Main Image" id="mainImage">
    </div>
    <div class="gallery-thumbnails">
        <img src="/images/dz.jpg" alt="Thumbnail dz" onclick="showImage('/images/dz.jpg')">
        <img src="/images/f1.jpg" alt="Thumbnail f1" onclick="showImage('/images/f1.jpg')">
        <img src="/images/rafting1.jpg" alt="Thumbnail rafting1" onclick="showImage('/images/rafting1.jpg')">
        <img src="/images/sm.jpg" alt="Thumbnail sm" onclick="showImage('/images/sm.jpg')">
    </div>
</div>

<script>
    function showImage(src) {
        document.getElementById('mainImage').src = src;
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
    }

    .gallery-main img {
        width: 100%;
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .gallery-thumbnails {
        display: flex;
        justify-content: center;
        gap: 10px;
        overflow-x: auto;
        width: 80%;
    }

    .gallery-thumbnails img {
        width: 100px;
        height: 75px;
        cursor: pointer;
        transition: transform 0.3s;
    }

    .gallery-thumbnails img:hover {
        transform: scale(1.1);
        border: 2px solid #ddd;
        border-radius: 5px;
    }
</style>
