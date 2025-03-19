<style>
    /* 基础样式 */
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-color: #f4f4f4;
    }

    h1 {
        text-align: center;
        margin-bottom: 20px;
    }

    /* 缩略图网格 */
    .gallery-thumbnails {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 15px;
        padding: 20px;
        max-width: 1200px;
        margin: 0 auto;
    }

    /* 缩略图框 */
    .thumbnail-container {
        position: relative;
        cursor: pointer;
        overflow: hidden;
        border-radius: 8px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        background: #e0e0e0;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    /* 图片填充整个框 */
    .thumbnail-container img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        border-radius: 8px;
        opacity: 0;
        transition: opacity 0.3s ease-in-out;
    }

    /* 图片加载完成后显示 */
    .thumbnail-container img.loaded {
        opacity: 1;
    }

    /* "加载中" 占位文本 */
    .thumbnail-container .loading-text {
        position: absolute;
        font-size: 14px;
        color: #666;
    }

    /* 模态框样式 */
    .modal {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.8);
        justify-content: center;
        align-items: center;
        z-index: 1000;
    }

    .modal-content {
        position: relative;
        max-width: 90%;
        max-height: 90%;
        background-color: #fff;
        border-radius: 8px;
        box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
        overflow: hidden;
    }

    .modal-content img {
        max-width: 100%;
        max-height: 80vh;
        display: block;
        margin: 0 auto;
    }

    /* 模态框中的导航按钮 */
    .modal-nav {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        font-size: 2em;
        padding: 10px 20px;
        cursor: pointer;
        z-index: 1;
        border-radius: 50%;
    }

    .modal-nav.left {
        left: 20px;
    }

    .modal-nav.right {
        right: 20px;
    }

    /* 关闭按钮 */
    .close-modal {
        position: absolute;
        top: 10px;
        right: 10px;
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        font-size: 1.5em;
        padding: 5px 10px;
        cursor: pointer;
        border-radius: 50%;
    }

    /* 模态框加载动画 */
    .modal-loading {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: 2;
    }

    .modal-loading .spinner {
        border: 4px solid rgba(0, 0, 0, 0.1);
        border-top: 4px solid #2196F3;
        border-radius: 50%;
        width: 40px;
        height: 40px;
        animation: spin 1s linear infinite;
    }

    @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }
</style>

<h1>Gallery</h1>
<div class="gallery-thumbnails" id="thumbnailContainer"></div>

<!-- 模态框 -->
<div class="modal" id="modal">
    <div class="modal-content">
        <button class="close-modal" onclick="closeModal()">&times;</button>
        <img src="" alt="Main Image" id="modalImage">
        <button class="modal-nav left" onclick="showPreviousImage()">&#10094;</button>
        <button class="modal-nav right" onclick="showNextImage()">&#10095;</button>
        <!-- 模态框加载动画 -->
        <div class="modal-loading" id="modalLoading">
            <div class="spinner"></div>
        </div>
    </div>
</div>

<script>
    let currentIndex = 0;
    let isPreloading = true; // 是否允许预加载
    const thumbnailBasePath = '/thumbnails/';
    const imageBasePath = '/images/';
    const imageFiles = [
        '1_清远漂流.jpg',
        '2_冬至.jpg',
        '3_石门1.jpg',
        '4_石门2.jpg',
        '5_石门3.jpg',
        '6_石门4.jpg',
        '7_红林花海.jpg',
        '8_羽毛球赛.jpg',
        '9_课题组合照_2024.jpg',
        '10_毕业典礼合照.jpg',
        '11_龙林毕业聚餐_2024.jpg',
        '12_大南山1.jpg',
        '13_大南山2.jpg',
        '14_大南山3.jpg',
        '15_大南山4.jpg',
        '16_大南山5.jpg',
        '17_大南山6.jpg'
    ];

    const images = imageFiles.map(fileName => ({
        thumbSrc: `${thumbnailBasePath}${fileName.replace(/\.(jpg|jpeg|png|webp)$/, '_t.$1')}`,
        src: `${imageBasePath}${fileName}`,
        alt: fileName.replace(/_/g, ' ').replace(/\..+$/, '')
    }));

    // 生成缩略图
    function generateThumbnails() {
        const container = document.getElementById('thumbnailContainer');
        container.innerHTML = '';
        images.forEach((img, index) => {
            const thumbnail = document.createElement('div');
            thumbnail.className = 'thumbnail-container';

            // 加载中提示
            const loadingText = document.createElement('div');
            loadingText.className = 'loading-text';
            loadingText.innerText = 'loading';
            thumbnail.appendChild(loadingText);

            // 创建图片元素
            const imageElement = document.createElement('img');
            imageElement.loading = 'lazy';
            imageElement.src = img.thumbSrc;
            imageElement.alt = `Thumbnail ${img.alt}`;

            // 图片加载完成后，隐藏“加载中”文本
            imageElement.onload = () => {
                imageElement.classList.add('loaded');
                loadingText.style.display = 'none';

                // 缩略图加载完成后，开始预加载大图
                if (index === images.length - 1) {
                    startPreloading();
                }
            };

            // 绑定点击事件
            thumbnail.onclick = () => openModal(index);
            thumbnail.appendChild(imageElement);
            container.appendChild(thumbnail);
        });
    }

    // 开始预加载大图
    function startPreloading() {
        let preloadIndex = 0;
        const preloadNext = () => {
            if (preloadIndex >= images.length || !isPreloading) return;

            const img = new Image();
            img.src = images[preloadIndex].src;
            img.onload = () => {
                console.log(`预加载完成: ${images[preloadIndex].src}`);
                preloadIndex++;
                preloadNext(); // 继续预加载下一张
            };
        };

        preloadNext();
    }

    // 打开模态框
    function openModal(index) {
        isPreloading = false; // 暂停预加载
        currentIndex = index;
        const modal = document.getElementById('modal');
        const modalImage = document.getElementById('modalImage');
        const modalLoading = document.getElementById('modalLoading');

        // 显示模态框和加载动画
        modal.style.display = 'flex';
        modalLoading.style.display = 'block';
        modalImage.style.opacity = 0;

        // 加载大图
        const img = new Image();
        img.src = images[index].src;
        img.onload = () => {
            modalImage.src = img.src;
            modalImage.alt = images[index].alt;
            modalImage.style.opacity = 1;
            modalLoading.style.display = 'none';

            // 当前大图加载完成后，恢复预加载
            isPreloading = true;
            startPreloading();
        };
    }

    // 关闭模态框
    function closeModal() {
        const modal = document.getElementById('modal');
        const modalImage = document.getElementById('modalImage');
        modal.style.display = 'none';
        modalImage.src = '';
    }

    // 切换到上一张图片
    function showPreviousImage() {
        currentIndex = (currentIndex - 1 + images.length) % images.length;
        loadImageIntoModal(currentIndex);
    }

    // 切换到下一张图片
    function showNextImage() {
        currentIndex = (currentIndex + 1) % images.length;
        loadImageIntoModal(currentIndex);
    }

    // 加载图片到模态框
    function loadImageIntoModal(index) {
        const modalImage = document.getElementById('modalImage');
        const modalLoading = document.getElementById('modalLoading');

        // 显示加载动画
        modalLoading.style.display = 'block';
        modalImage.style.opacity = 0;

        // 加载大图
        const img = new Image();
        img.src = images[index].src;
        img.onload = () => {
            modalImage.src = img.src;
            modalImage.alt = images[index].alt;
            modalImage.style.opacity = 1;
            modalLoading.style.display = 'none';
        };
    }

    // 键盘切换功能
    document.addEventListener('keydown', (e) => {
        const modal = document.getElementById('modal');
        if (modal.style.display === 'flex') {
            if (e.key === 'ArrowLeft') showPreviousImage();
            if (e.key === 'ArrowRight') showNextImage();
            if (e.key === 'Escape') closeModal();
        }
    });

    // 初始化
    document.addEventListener('DOMContentLoaded', () => {
        generateThumbnails();
    });
</script>