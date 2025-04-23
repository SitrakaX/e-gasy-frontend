<script setup>
import { onMounted, ref } from 'vue';

const slides = ref([]);
const currentIndex = ref(0);

function showSlide(index) {
    slides.value.forEach((slide, i) => {
        slide.classList.remove('active');
        if (i === index) slide.classList.add('active');
    });
}

onMounted(() => {
    slides.value = document.querySelectorAll('.slide');

    document.querySelector('.arrow.left').addEventListener('click', () => {
        currentIndex.value = (currentIndex.value > 0) ? currentIndex.value - 1 : slides.value.length - 1;
        showSlide(currentIndex.value);
    });

    document.querySelector('.arrow.right').addEventListener('click', () => {
        currentIndex.value = (currentIndex.value + 1) % slides.value.length;
        showSlide(currentIndex.value);
    });

    // Affiche la première diapositive par défaut
    showSlide(currentIndex.value);
});
</script>

<template>
    <div class="w-full relative z-0">
        <div class="carousel w-full">
            <div class="slide">
                <div
                    class="text absolute z-10 text-white text-2xl font-bold top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
                    Texte 1</div>
                <img src="https://picsum.photos/1080/200?random=1" alt="Image 1" class="w-full h-auto">
            </div>
            <div class="slide">
                <div
                    class="text absolute z-10 text-white text-2xl font-bold top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
                    Texte 2</div>
                <img src="https://picsum.photos/1080/200?random=2" alt="Image 2" class="w-full h-auto">
            </div>
            <button class="arrow left bg-black/30 text-white p-2 rounded-full">◄</button>
            <button class="arrow right bg-black/30 text-white p-2 rounded-full">►</button>
        </div>
    </div>
</template>

<style>
.carousel {
    position: relative;
    overflow: hidden;
    margin: 0 auto;
}

.slide {
    display: none;
    text-align: center;
    position: relative;
}

.slide.active {
    display: block;
}

.slide.active .text {
    animation: showText 1s forwards;
}

.slide.active img {
    animation: showImage 1s forwards;
    width: 100%;
}

@keyframes showText {
    from {
        opacity: 0;
        transform: translate(-50%, -70%);
    }

    to {
        opacity: 1;
        transform: translate(-50%, -50%);
    }
}

@keyframes showImage {
    from {
        opacity: 0.7;
    }

    to {
        opacity: 1;
    }
}

.arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    cursor: pointer;
    z-index: 20;
}

.arrow.left {
    left: 20px;
}

.arrow.right {
    right: 20px;
}
</style>
