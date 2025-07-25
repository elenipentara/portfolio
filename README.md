<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eleni Pentara - Theatre & Visual Arts</title>
    <meta name="description" content="Eleni Pentara - Theatre director and visual artist. Portfolio showcasing Metamorfosi della terra, Ulises Agreste, Cyborg-phagy and visual arts.">
    <meta name="keywords" content="Eleni Pentara, theatre, visual arts, director, performance, art">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Adobe Garamond Pro', 'Garamond', 'Times New Roman', serif;
            background: #ffffff;
            color: #000000;
            line-height: 1.6;
            padding: 120px 160px 40px;
        }

        .navigation {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        h1 {
            font-size: 48px;
            font-weight: 300;
            letter-spacing: 2px;
            margin-bottom: 40px;
            cursor: pointer;
            background: none;
            padding: 0;
            display: block;
            text-transform: uppercase;
            color: #666;
            text-align: center;
        }

        .categories-row {
            display: flex;
            gap: 40px;
            margin-bottom: 60px;
            align-items: center;
            justify-content: center;
        }

        .category {
            font-size: 22px;
            font-weight: 100;
            color: #666;
            cursor: pointer;
            transition: all 0.3s ease;
            font-style: normal;
        }

        .category:hover,
        .category.active {
            font-family: 'Garamond Premier Pro', 'Adobe Garamond Pro', 'Garamond', 'Times New Roman', serif;
            font-weight: 700;
            font-style: normal;
            letter-spacing: 0.5px;
        }

        .category-divider {
            color: #999;
            font-size: 18px;
            font-weight: 100;
        }

        .items {
            display: none;
            flex-direction: column;
            gap: 10px;
            margin-top: 20px;
            align-items: center;
        }

        .items.show {
            display: flex;
        }

        .item {
            font-size: 20px;
            font-weight: 300;
            color: #000000;
            cursor: pointer;
            transition: all 0.3s ease;
            font-style: normal;
            white-space: nowrap;
            letter-spacing: 0.5px;
        }

        .item:hover {
            font-weight: 700;
            letter-spacing: 1px;
        }

        .email {
            cursor: default;
        }

        .email:hover {
            font-weight: 300;
            letter-spacing: 0.5px;
        }

        /* Visual Arts Slideshow */
        .slideshow {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: #ffffff;
            z-index: 100;
            padding: 0;
        }

        .slideshow.show {
            display: block;
        }

        .slideshow-container {
            position: relative;
            background: #ffffff;
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        .slideshow-image {
            max-width: 60vw;
            max-height: 70vh;
            object-fit: contain;
            cursor: pointer;
            background: #ffffff;
            display: none;
            margin-bottom: 40px;
        }

        .slideshow-image.active {
            display: block;
        }

        .slide-nav {
            position: absolute;
            bottom: 60px;
            background: none;
            border: none;
            font-size: 20px;
            font-family: 'Adobe Garamond Pro', 'Garamond', 'Times New Roman', serif;
            font-weight: 300;
            color: #666;
            cursor: pointer;
            transition: color 0.3s ease;
            text-decoration: none;
        }

        .slide-nav:hover {
            color: #000;
        }

        .slide-prev {
            left: 45%;
        }

        .slide-next {
            right: 45%;
        }

        .slide-info {
            font-size: 18px;
            font-weight: 300;
            color: #666;
            font-style: italic;
            position: absolute;
            bottom: 100px;
            left: 50%;
            transform: translateX(-50%);
            text-align: center;
            white-space: nowrap;
        }

        /* Modal for full-size image */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            cursor: pointer;
        }

        .modal-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            max-width: 90%;
            max-height: 90%;
            object-fit: contain;
        }

        .close {
            position: absolute;
            top: 20px;
            right: 35px;
            color: #f1f1f1;
            font-size: 40px;
            font-weight: bold;
            cursor: pointer;
        }

        .close:hover {
            opacity: 0.7;
        }

        .back-arrow {
            font-size: 16px;
            color: #666;
            cursor: pointer;
            transition: color 0.3s ease;
            position: absolute;
            top: 40px;
            left: 40px;
            text-decoration: underline;
            font-family: 'Adobe Garamond Pro', 'Garamond', 'Times New Roman', serif;
            font-weight: 300;
        }

        .back-arrow:hover {
            color: #000;
        }

        @media (max-width: 768px) {
            body {
                padding: 100px 20px 40px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            .categories-row {
                flex-direction: column;
                gap: 20px;
            }
            
            .category-divider {
                display: none;
            }
            
            .items {
                gap: 15px;
            }

            .slideshow-image {
                max-width: 90vw;
                max-height: 60vh;
            }

            .slide-prev {
                left: 20%;
            }

            .slide-next {
                right: 20%;
            }

            .slide-info {
                font-size: 12px;
                white-space: normal;
                max-width: 80%;
                line-height: 1.3;
            }
        }
    </style>
</head>
<body>
    <div class="navigation">
        <h1 onclick="hideAll()">eleni pentara</h1>
        
        <div class="categories-row">
            <span class="category" id="visual-category" onclick="showVisual()">visual arts</span>
            <span class="category-divider">|</span>
            <span class="category" id="theatre-category" onclick="showTheatre()">theatre</span>
            <span class="category-divider">|</span>
            <span class="category" id="contact-category" onclick="showContact()">contact</span>
        </div>
        
        <div class="items" id="theatre">
            <span class="item" onclick="showMetamorfosi()">Metamorfosi della terra 2025</span>
            <span class="item" onclick="showUlises()">Ulises Agreste 2024</span>
            <span class="item" onclick="showCyborg()">Cyborg-phagy 2023</span>
        </div>
        
        <div class="items" id="contact">
            <span class="item email">elenipentara@hotmail.com</span>
        </div>
        
        <!-- Visual Arts Slideshow -->
        <div class="slideshow" id="visual-slideshow">
            <div class="slideshow-container">
                <img src="https://i.imgur.com/R8jyft7.jpeg" alt="humankind sketch" class="slideshow-image active" onclick="openModal(this.src, 'VISUAL ART / SKETCH / humankind')">
                <img src="https://i.imgur.com/tTeynfX.jpeg" alt="Bah Voilà comic" class="slideshow-image" onclick="openModal(this.src, 'VISUAL ART / COMIC / Bah Voilà')">
                <img src="https://i.imgur.com/A7AeJE8.png" alt="Man enters & exits storyboard" class="slideshow-image" onclick="openModal(this.src, 'VISUAL ART / STORYBOARDING / Man enters & exits')">
                
                <button class="slide-nav slide-prev" onclick="changeSlide(-1)">←</button>
                <button class="slide-nav slide-next" onclick="changeSlide(1)">→</button>
            </div>
            <div class="slide-info" id="slide-caption">VISUAL ART / SKETCH / humankind</div>
            <div class="back-arrow" onclick="hideAll();">← back</div>
        </div>
    </div>
    
    <!-- Ulises Agreste Slideshow -->
    <div class="slideshow" id="ulises-slideshow">
        <div class="slideshow-container">
            <img src="https://i.imgur.com/HkdKgbu.jpeg" alt="Ulises Agreste Performance 1" class="slideshow-image active" onclick="openModal(this.src, 'PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024')">
            <img src="https://i.imgur.com/iwIk7D6.jpeg" alt="Ulises Agreste Performance 2" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024')">
            <img src="https://i.imgur.com/tPutqKe.jpeg" alt="Ulises Agreste Performance 3" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024')">
            <img src="https://i.imgur.com/U4MnCfL.jpeg" alt="Ulises Agreste Performance 4" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024')">
            <img src="https://i.imgur.com/su3gvOJ.jpeg" alt="Ulises Agreste Performance 5" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024')">
            <img src="https://i.imgur.com/U7OsS83.jpeg" alt="Ulises Agreste Performance 6" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024')">
            <img src="https://i.imgur.com/N6JsG7j.jpeg" alt="Ulises Agreste Performance 7" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024')">
            
            <button class="slide-nav slide-prev" onclick="changeUlisesSlide(-1)">←</button>
            <button class="slide-nav slide-next" onclick="changeUlisesSlide(1)">→</button>
        </div>
        <div class="slide-info">PHOTOS: JÚLIO COELHO / PRODUCTION Ulises Agreste / 2024</div>
        <div class="back-arrow" onclick="hideAll(); showTheatre();">← back</div>
    </div>
    
    <!-- Metamorfosi della terra Slideshow -->
    <div class="slideshow" id="metamorfosi-slideshow">
        <div class="slideshow-container">
            <img src="https://i.imgur.com/ilh8QRt.jpeg" alt="Metamorfosi della terra Performance 1" class="slideshow-image active" onclick="openModal(this.src, 'PHOTO: CHIARA HERRERIAS STADE / SOLO PIECE / PRODUCTION Metamorfosi della terra / 2025')">
            <img src="https://i.imgur.com/3Vcc4Ij.jpeg" alt="Metamorfosi della terra Performance 2" class="slideshow-image" onclick="openModal(this.src, 'PHOTO: CHIARA HERRERIAS STADE / SOLO PIECE / PRODUCTION Metamorfosi della terra / 2025')">
            <img src="https://i.imgur.com/z62x4YC.jpeg" alt="Metamorfosi della terra Performance 3" class="slideshow-image" onclick="openModal(this.src, 'PHOTO: CHIARA HERRERIAS STADE / SOLO PIECE / PRODUCTION Metamorfosi della terra / 2025')">
            <img src="https://i.imgur.com/0vEcDN6.jpeg" alt="Metamorfosi della terra Performance 4" class="slideshow-image" onclick="openModal(this.src, 'PHOTO: CHIARA HERRERIAS STADE / SOLO PIECE / PRODUCTION Metamorfosi della terra / 2025')">
            <img src="https://i.imgur.com/yK4f6zf.jpeg" alt="Metamorfosi della terra Performance 5" class="slideshow-image" onclick="openModal(this.src, 'PHOTO: CHIARA HERRERIAS STADE / SOLO PIECE / PRODUCTION Metamorfosi della terra / 2025')">
            
            <button class="slide-nav slide-prev" onclick="changeMetamorfosiSlide(-1)">←</button>
            <button class="slide-nav slide-next" onclick="changeMetamorfosiSlide(1)">→</button>
        </div>
        <div class="slide-info">PHOTO: CHIARA HERRERIAS STADE / SOLO PIECE / PRODUCTION Metamorfosi della terra / 2025</div>
        <div class="back-arrow" onclick="hideAll(); showTheatre();">← back</div>
    </div>
    
    <!-- Cyborg-phagy Slideshow -->
    <div class="slideshow" id="cyborg-slideshow">
        <div class="slideshow-container">
            <img src="https://i.imgur.com/pX5nvML.jpeg" alt="Cyborg-phagy Performance 1" class="slideshow-image active" onclick="openModal(this.src, 'PHOTOS: CHIARA HERRERIAS STADE / PRODUCTION Cyborg-phagy / 2023')">
            <img src="https://i.imgur.com/P04W9fe.jpeg" alt="Cyborg-phagy Performance 2" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: CHIARA HERRERIAS STADE / PRODUCTION Cyborg-phagy / 2023')">
            <img src="https://i.imgur.com/sO0Ut0X.jpeg" alt="Cyborg-phagy Performance 3" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: CHIARA HERRERIAS STADE / PRODUCTION Cyborg-phagy / 2023')">
            <img src="https://i.imgur.com/0u5k9z8.jpeg" alt="Cyborg-phagy Performance 4" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: CHIARA HERRERIAS STADE / PRODUCTION Cyborg-phagy / 2023')">
            <img src="https://i.imgur.com/ArvQ5oi.jpeg" alt="Cyborg-phagy Performance 5" class="slideshow-image" onclick="openModal(this.src, 'PHOTOS: CHIARA HERRERIAS STADE / PRODUCTION Cyborg-phagy / 2023')">
            
            <button class="slide-nav slide-prev" onclick="changeCyborgSlide(-1)">←</button>
            <button class="slide-nav slide-next" onclick="changeCyborgSlide(1)">→</button>
        </div>
        <div class="slide-info">PHOTOS: CHIARA HERRERIAS STADE / PRODUCTION Cyborg-phagy / 2023</div>
        <div class="back-arrow" onclick="hideAll(); showTheatre();">← back</div>
    </div>

    <!-- Modal for full-size image -->
    <div id="imageModal" class="modal" onclick="closeModal()">
        <span class="close" onclick="closeModal()">&times;</span>
        <img class="modal-content" id="modalImage" src="">
    </div>

    <script>
        let currentSlideIndex = 0;
        let currentCyborgSlideIndex = 0;
        let currentMetamorfosiSlideIndex = 0;
        let currentUlisesSlideIndex = 0;
        const slides = document.querySelectorAll('#visual-slideshow .slideshow-image');
        const cyborgSlides = document.querySelectorAll('#cyborg-slideshow .slideshow-image');
        const metamorfosiSlides = document.querySelectorAll('#metamorfosi-slideshow .slideshow-image');
        const ulisesSlides = document.querySelectorAll('#ulises-slideshow .slideshow-image');
        const captions = [
            'VISUAL ART / SKETCH / humankind',
            'VISUAL ART / COMIC / Bah Voilà',
            'VISUAL ART / STORYBOARDING / Man enters & exits'
        ];

        function hideAll() {
            document.getElementById('theatre').classList.remove('show');
            document.getElementById('contact').classList.remove('show');
            document.getElementById('visual-slideshow').classList.remove('show');
            document.getElementById('cyborg-slideshow').classList.remove('show');
            document.getElementById('metamorfosi-slideshow').classList.remove('show');
            document.getElementById('ulises-slideshow').classList.remove('show');
            document.querySelector('.navigation').style.display = 'flex';
            
            // Remove active states
            document.getElementById('visual-category').classList.remove('active');
            document.getElementById('theatre-category').classList.remove('active');
            document.getElementById('contact-category').classList.remove('active');
        }

        function showVisual() {
            hideAll();
            document.getElementById('visual-slideshow').classList.add('show');
            document.querySelector('.navigation').style.display = 'flex';
            document.getElementById('visual-category').classList.add('active');
        }

        function showTheatre() {
            hideAll();
            document.getElementById('theatre').classList.add('show');
            document.querySelector('.navigation').style.display = 'flex';
            document.getElementById('theatre-category').classList.add('active');
        }

        function showContact() {
            hideAll();
            document.getElementById('contact').classList.add('show');
            document.querySelector('.navigation').style.display = 'flex';
            document.getElementById('contact-category').classList.add('active');
        }

        function showUlises() {
            document.getElementById('theatre').classList.remove('show');
            document.getElementById('contact').classList.remove('show');
            document.getElementById('visual-slideshow').classList.remove('show');
            document.getElementById('cyborg-slideshow').classList.remove('show');
            document.getElementById('metamorfosi-slideshow').classList.remove('show');
            document.getElementById('ulises-slideshow').classList.add('show');
            document.querySelector('.navigation').style.display = 'none';
            
            // Keep theatre active
            document.getElementById('visual-category').classList.remove('active');
            document.getElementById('theatre-category').classList.add('active');
            document.getElementById('contact-category').classList.remove('active');
            
            // Reset to first slide
            currentUlisesSlideIndex = 0;
            ulisesSlides.forEach((slide, index) => {
                slide.classList.remove('active');
                if (index === 0) slide.classList.add('active');
            });
        }

        function showMetamorfosi() {
            document.getElementById('theatre').classList.remove('show');
            document.getElementById('contact').classList.remove('show');
            document.getElementById('visual-slideshow').classList.remove('show');
            document.getElementById('cyborg-slideshow').classList.remove('show');
            document.getElementById('metamorfosi-slideshow').classList.add('show');
            document.querySelector('.navigation').style.display = 'none';
            
            // Keep theatre active
            document.getElementById('visual-category').classList.remove('active');
            document.getElementById('theatre-category').classList.add('active');
            document.getElementById('contact-category').classList.remove('active');
            
            // Reset to first slide
            currentMetamorfosiSlideIndex = 0;
            metamorfosiSlides.forEach((slide, index) => {
                slide.classList.remove('active');
                if (index === 0) slide.classList.add('active');
            });
        }

        function showCyborg() {
            document.getElementById('theatre').classList.remove('show');
            document.getElementById('contact').classList.remove('show');
            document.getElementById('visual-slideshow').classList.remove('show');
            document.getElementById('metamorfosi-slideshow').classList.remove('show');
            document.getElementById('cyborg-slideshow').classList.add('show');
            document.querySelector('.navigation').style.display = 'none';
            
            // Keep theatre active
            document.getElementById('visual-category').classList.remove('active');
            document.getElementById('theatre-category').classList.add('active');
            document.getElementById('contact-category').classList.remove('active');
            
            // Reset to first slide
            currentCyborgSlideIndex = 0;
            cyborgSlides.forEach((slide, index) => {
                slide.classList.remove('active');
                if (index === 0) slide.classList.add('active');
            });
        }

        function changeSlide(direction) {
            slides[currentSlideIndex].classList.remove('active');
            
            currentSlideIndex += direction;
            if (currentSlideIndex >= slides.length) currentSlideIndex = 0;
            if (currentSlideIndex < 0) currentSlideIndex = slides.length - 1;
            
            slides[currentSlideIndex].classList.add('active');
            document.getElementById('slide-caption').textContent = captions[currentSlideIndex];
        }

        function changeCyborgSlide(direction) {
            cyborgSlides[currentCyborgSlideIndex].classList.remove('active');
            
            currentCyborgSlideIndex += direction;
            if (currentCyborgSlideIndex >= cyborgSlides.length) currentCyborgSlideIndex = 0;
            if (currentCyborgSlideIndex < 0) currentCyborgSlideIndex = cyborgSlides.length - 1;
            
            cyborgSlides[currentCyborgSlideIndex].classList.add('active');
        }

        function changeMetamorfosiSlide(direction) {
            metamorfosiSlides[currentMetamorfosiSlideIndex].classList.remove('active');
            
            currentMetamorfosiSlideIndex += direction;
            if (currentMetamorfosiSlideIndex >= metamorfosiSlides.length) currentMetamorfosiSlideIndex = 0;
            if (currentMetamorfosiSlideIndex < 0) currentMetamorfosiSlideIndex = metamorfosiSlides.length - 1;
            
            metamorfosiSlides[currentMetamorfosiSlideIndex].classList.add('active');
        }

        function changeUlisesSlide(direction) {
            ulisesSlides[currentUlisesSlideIndex].classList.remove('active');
            
            currentUlisesSlideIndex += direction;
            if (currentUlisesSlideIndex >= ulisesSlides.length) currentUlisesSlideIndex = 0;
            if (currentUlisesSlideIndex < 0) currentUlisesSlideIndex = ulisesSlides.length - 1;
            
            ulisesSlides[currentUlisesSlideIndex].classList.add('active');
        }

        function openModal(imageSrc, caption) {
            document.getElementById('imageModal').style.display = 'block';
            document.getElementById('modalImage').src = imageSrc;
        }

        function closeModal() {
            document.getElementById('imageModal').style.display = 'none';
        }

        // Keyboard navigation and modal controls
        document.addEventListener('keydown', function(event) {
            if (event.key === 'Escape') {
                closeModal();
            }
            
            // Keyboard navigation for slideshows
            if (document.getElementById('visual-slideshow').classList.contains('show')) {
                if (event.key === 'ArrowLeft') {
                    changeSlide(-1);
                } else if (event.key === 'ArrowRight') {
                    changeSlide(1);
                }
            }
            
            if (document.getElementById('ulises-slideshow').classList.contains('show')) {
                if (event.key === 'ArrowLeft') {
                    changeUlisesSlide(-1);
                } else if (event.key === 'ArrowRight') {
                    changeUlisesSlide(1);
                }
            }
            
            if (document.getElementById('metamorfosi-slideshow').classList.contains('show')) {
                if (event.key === 'ArrowLeft') {
                    changeMetamorfosiSlide(-1);
                } else if (event.key === 'ArrowRight') {
                    changeMetamorfosiSlide(1);
                }
            }
            
            if (document.getElementById('cyborg-slideshow').classList.contains('show')) {
                if (event.key === 'ArrowLeft') {
                    changeCyborgSlide(-1);
                } else if (event.key === 'ArrowRight') {
                    changeCyborgSlide(1);
                }
            }
        });
    </script>
</body>
</html>
