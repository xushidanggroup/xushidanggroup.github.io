---
title: Gallery
date: 2023-06-19T12:00:00Z
---

<style>
    h1 {
        text-align: center;
        margin-bottom: 2px; /* Reduce the margin below the title */
    }

    .gallery {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 3px; /* Reduce the margin above the gallery */
    }

    .gallery-thumbnails {
        display: flex;
        justify-content: flex-start; /* Align thumbnails to the left */
        gap: 10px; /* Reduce the gap between thumbnails */
        overflow-x: auto; /* Add a horizontal scrollbar */
        white-space: nowrap; /* Prevent thumbnails from wrapping */
        width: 100%; /* Use a larger area to display thumbnails */
        margin-bottom: 2px; /* Reduce the margin between thumbnails and description */
        padding: 5px; /* Add padding to make the scrollbar more visible */
        box-sizing: border-box;
    }

    .thumbnail-container {
        display: inline-flex; /* Make the container an inline block element */
        flex-direction: column;
        align-items: center;
        cursor: pointer;
    }

    .thumbnail-container img {
        width: 130px; /* Adjust the width of the thumbnails */
        height: 90px; /* Adjust the height of the thumbnails */
        transition: transform 0.3s;
    }

    .thumbnail-container img:hover {
        transform: scale(1.1);
        border: 2px solid #ddd;
        border-radius: 5px;
    }

    .thumbnail-container p {
        margin-top: 2px; /* Reduce the margin between the description and the thumbnail */
        font-size: 0.9em; /* Adjust the size of the description text */
        color: #777;
        text-align: center;
    }

    .gallery-main {
        width: 100%; /* Utilize the width of the parent container */
        max-width: 90vw; /* Set the maximum width to 90% of the viewport width */
        text-align: center;
        position: relative;
        margin: 0 auto; /* Center horizontally */
    }

    .gallery-main img {
        max-width: 100%; /* Make the image's max width 100% to prevent stretching on smaller screens */
        height: auto;
        border: 2px solid #ddd;
        border-radius: 5px;
        transition: opacity 2s ease-in-out; /* Transition effect duration */
        opacity: 1;
    }

    #mainImageDescription {
        margin-top: 2px; /* Reduce the margin between the description and the thumbnail */
        margin-bottom: 2px; /* Reduce the margin between the description and the main image */
        font-size: 1em; /* Adjust the size of the description text */
        color: #555;
        transition: opacity 2s ease-in-out; /* Increase the transition effect duration to 2 seconds */
        opacity: 1;
    }

    .gallery-nav {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        font-size: 2em; /* Adjust the size of the navigation buttons */
        padding: 10px; /* Increase the padding of the buttons */
        cursor: pointer;
        z-index: 1;
    }

    .gallery-nav.left {
        left: 0;
    }

    .gallery-nav.right {
        right: 0;
    }

    /* Add scrollbar styles */
    .gallery-thumbnails::-webkit-scrollbar {
        height: 8px; /* Height of the scrollbar */
    }

    .gallery-thumbnails::-webkit-scrollbar-thumb {
        background: #888; /* Color of the scrollbar */
        border-radius: 4px;
    }

    .gallery-thumbnails::-webkit-scrollbar-thumb:hover {
        background: #555; /* Color of the scrollbar on hover */
    }

    .gallery-thumbnails::-webkit-scrollbar-track {
        background: #f1f1f1; /* Color of the scrollbar track */
    }
</style>

<div class="gallery">
    <div class="gallery-thumbnails">
        <div class="thumbnail-container" onclick="showImage(0, true)">
            <img src="/images/dz.jpg" alt="Thumbnail dz">
        </div>
        <div class="thumbnail-container" onclick="showImage(1, true)">
            <img src="/images/f1.jpg" alt="Thumbnail f1">
        </div>
        <div class="thumbnail-container" onclick="showImage(2, true)">
            <img src="/images/rafting1.jpg" alt="Thumbnail rafting1">
        </div>
        <div class="thumbnail-container" onclick="showImage(3, true)">
            <img src="/images/sm.jpg" alt="Thumbnail sm">
        </div>
        <div class="thumbnail-container" onclick="showImage(4, true)">
            <img src="/images/课题组合照.jpg" alt="Thumbnail 课题组合照">
        </div>
        <div class="thumbnail-container" onclick="showImage(5, true)">
            <img src="/images/毕业典礼合照.jpg" alt="Thumbnail 毕业典礼合照">
        </div>
        <div class="thumbnail-container" onclick="showImage(6, true)">
            <img src="/images/龙林毕业聚餐.jpg" alt="Thumbnail 龙林毕业聚餐">
        </div>
        <div class="thumbnail-container" onclick="showImage(7, true)">
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
            src: '/images/f1.jpg',
            description: 'Camping trip at Shimen - Jan 7, 2024'
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
    const transitionTime = 1500; // 2 seconds
    const quickTransitionTime = 500; // 0.5 seconds

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

        // Fade-out effect
        mainImage.style.opacity = 0;
        mainImageDescription.style.opacity = 0;

        setTimeout(() => {
            mainImage.src = images[index].src;
            mainImageDescription.textContent = images[index].description;

            // Fade-in effect
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
        autoSwitchInterval = setInterval(showNextImage, 5000); // Change interval time to 5000 milliseconds (5 seconds)
    }

    function resetAutoSwitch() {
        clearInterval(autoSwitchInterval);
        autoSwitchImages();
    }

    document.addEventListener('DOMContentLoaded', () => {
        autoSwitchImages();
    });
</script>
