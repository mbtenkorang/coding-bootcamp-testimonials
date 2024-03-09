<script setup>
import { ref, computed } from 'vue';


const currentSlideIndex = ref(0)
const currentSlide = computed(() => testimonialdata.value[currentSlideIndex.value])

const previousSlide = () => {
  currentSlideIndex.value = (currentSlideIndex.value - 1 + testimonialdata.value.length) % testimonialdata.value.length;
};

const nextSlide = () => {
  currentSlideIndex.value = (currentSlideIndex.value + 1) % testimonialdata.value.length;
}

const testimonialdata = ref([{
  user_name: " John Tarkpor",
  user_role: "Junior Front-end Developer",
  "user_testimonial": " If you want to lay the best foundation possible I’d recommend taking this course.\
  The depth the instructors go into is incredible. I now feel so confident about \
  starting up as a professional developer. ",
  "imageUrl": "./images/image-john.jpg"
},
{
  user_name: "Tanya Sinclair",
  user_role: "UX Engineer",
  "user_testimonial": " I’ve been interested in coding for a while but never taken the jump, until now.\
  I couldn’t recommend this course enough. I’m now in the job of my dreams and so\
  excited about the future.",
  "imageUrl": "./images/image-tanya.jpg"
},])

</script>

<template>
  <div>
    <article>
      <div class="image-container">
        <img :src="currentSlide.imageUrl" :alt="currentSlide.user_name">
        <div class="nav-buttons">
          <span role="button" @click="previousSlide" aria-label="previous testimonial">
            <img src="./assets/icon-prev.svg" alt="">
          </span>
          <span role="button" @click="nextSlide" aria-label="next testimonial">
            <img src="./assets/icon-next.svg" alt="">
          </span>
        </div>
      </div>
      <div>
        <p>{{ currentSlide.user_testimonial }}</p>
        <h1>{{ currentSlide.user_name }}</h1>
        <p>{{ currentSlide.user_role }}</p>
      </div>

    </article>

  </div>
</template>

<style scoped>
img {
  max-width: 50%;
  display: block;
}

.image-container {
  position: relative;
  background-image: url("./images/pattern-bg.svg");
  background-repeat: no-repeat;
}

.nav-buttons {
  position: absolute;
  bottom: -1rem;
}
</style>
