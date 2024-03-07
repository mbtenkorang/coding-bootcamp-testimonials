<script setup>
import { ref, computed } from 'vue';

const currentIndex = ref(0)
const currentSlide = computed(() => slides.value[currentIndex.value])

const nextSlide = () => {
    currentIndex.value = (currentIndex.value + 1) % slides.value.length;
}

const previousSlide = () => {
    currentIndex.value = (currentIndex.value - 1 + slide.value.length) % slide.value.lenght
}
</script>

<template>
    <div>
        <a href="">
            <img src="./images/icon-next.svg" alt="">
            <img src="./images/icon-prev.svg" alt="">
        </a>
        <a href=""></a>
    </div>
</template>