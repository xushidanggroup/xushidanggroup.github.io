---
title:
date: 2023-06-19T12:00:00Z
---

<style>
    h1 {
        text-align: center;
    }

    .slideshow-container {
        max-width: 1000px;
        position: relative;
        margin: auto;
    }

    .mySlides {
        display: none;
    }

    .mySlides img {
        width: 100%;
    }

    .prev, .next {
        cursor: pointer;
        position: absolute;
        top: 50%;
        width: auto;
        padding: 16px;
        margin-top: -22px;
        color: white;
        font-weight: bold;
        font-size: 18px;
        transition: 0.6s ease;
        border-radius: 0 3px 3px 0;
        user-select: none;
    }

    .next {
        right: 0;
        border-radius: 3px 0 0 3px;
    }

    .prev:hover, .next:hover {
        background-color: rgba(0,0,0,0.8);
    }

    .text {
        color: #555;
        font-size: 15px;
        padding: 8px 12px;
        position: absolute;
        bottom: 8px;
        width: 100%;
        text-align: center;
    }

    .numbertext {
        color: #f2f2f2;
        font-size: 12px;
        padding: 8px 12px;
        position: absolute;
        top: 0;
    }

    .dot {
        cursor: pointer;
        height: 15px;
        width: 15px;
        margin: 0 2px;
        background-color: #bbb;
        border-radius: 50%;
        display: inline-block;
        transition: background-color 0.6s ease;
    }

    .active, .dot:hover {
        background-color: #717171;
    }

    .fade {
        -webkit-animation-name: fade;
        -webkit-animation-duration: 1.5s;
        animation-name: fade;
        animation-duration: 1.5s;
    }

    @-webkit-keyframes fade {
        from {opacity: .4}
        to {opacity: 1}
    }

    @keyframes fade {
        from {opacity: .4}
        to {opacity: 1}
    }
</style>

<h1>Welcome to Our Website</h1>

<div class="slideshow-container">
    <div class="mySlides fade">
        <div class="numbertext">1 / 3</div>
        <img src="/static/images/cca.jpg" alt="Image 1">
        <div class="text">Mitochondria-targeting AIE photosensitizer is specifically synthesized inside cancer cells, realizing precise photodynamic therapy</div>
    </div>

    <div class="mySlides fade">
        <div class="numbertext">2 / 3</div>
        <img src="/static/images/psr.jpg" alt="Image 2">
        <div class="text">The first lipid droplet (LD)/nucleus dual-targeted ratiometric fluorescence probe, CQPP, for monitoring polarity change was developed.</div>
    </div>

    <div class="mySlides fade">
        <div class="numbertext">3 / 3</div>
        <img src="/static/images/r.jpg" alt="Image 3">
        <div class="text">The design principles of AIE PSs and their biomedical applications are discussed in detail.</div>
    </div>

    <a class="prev" onclick="plusSlides(-1)">&#10094;</a>
    <a class="next" onclick="plusSlides(1)">&#10095;</a>
</div>
<br>

<div style="text-align:center">
    <span class="dot" onclick="currentSlide(1)"></span> 
    <span class="dot" onclick="currentSlide(2)"></span> 
    <span class="dot" onclick="currentSlide(3)"></span> 
</div>

<script>
    let slideIndex = 1;
    showSlides(slideIndex);

    function plusSlides(n) {
        showSlides(slideIndex += n);
    }

    function currentSlide(n) {
        showSlides(slideIndex = n);
    }

    function showSlides(n) {
        let i;
        let slides = document.getElementsByClassName("mySlides");
        let dots = document.getElementsByClassName("dot");
        if (n > slides.length) {slideIndex = 1}    
        if (n < 1) {slideIndex = slides.length}
        for (i = 0; i < slides.length; i++) {
            slides[i].style.display = "none";  
        }
        for (i = 0; i < dots.length; i++) {
            dots[i].className = dots[i].className.replace(" active", "");
        }
        slides[slideIndex-1].style.display = "block";  
        dots[slideIndex-1].className += " active";
    }
</script>
