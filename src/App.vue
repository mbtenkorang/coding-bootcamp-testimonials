<script setup>
import { ref, computed } from 'vue';
import ProfileImage from './components/ProfileImage.vue';
import Testimonial from './components/Testimonial.vue';

const currentSlideIndex = ref(0);
const currentSlide = computed(() => testimonialData.value[currentSlideIndex.value])

const previousSlide = () => {
  currentSlideIndex.value = (currentSlideIndex.value - 1 + testimonialData.value.length) % testimonialData.value.length;
};

const nextSlide = () => {
  currentSlideIndex.value = (currentSlideIndex.value + 1) % testimonialData.value.length;
}

const testimonialData = ref([
  {
    "username": "John Tarkpor",
    "userrole": "Junior Front-end Developer",
    "testimonial": "If you want to lay the best foundation possible I'd recommend taking this course. The depth the instructors go into is incredible. I now feel so confident about starting up as a professional developer.",
    "imageurl": "/images/image-john.jpg"
  },
  {
    "username": "Tanya Sinclair",
    "userrole": "UX Engineer",
    "testimonial": "I've been interested in coding for a while but never taken the jump, until now. I couldn’t recommend this course enough. I’m now in the job of my dreams and so excited about the future.",
    "imageurl": "/images/image-tanya.jpg"
  }
]);

</script>


<template>

  <article class="b-slide__main__container">
    <!-- Testimonial Image -->
    <div class="b-slide__header__container">
      <div class="b-slide__image__container">
        <ProfileImage :imageurl="currentSlide.imageurl" :username="currentSlide.username" />
        <!-- Navigation Buttons -->
        <div class="b-nav--bar">
          <button role="button" @click="previousSlide" aria-labelledby="previous slide" class="b-button b-button__left">

          </button>

          <button type="button" @click="nextSlide" aria-labelledby="next slide" class="b-button b-button__right">

          </button>
        </div>

      </div>
    </div>

    <!-- Testimonial Text and Attribution -->
    <Testimonial :usertestimonial="currentSlide.testimonial" :username="currentSlide.username"
      :userrole="currentSlide.userrole" />
  </article>

</template>


<style>
.b-slide__main__container {
  display: grid;
  grid-template-rows: repeat(2, 1fr);
  background: 42% top / 92% no-repeat url("/images/pattern-bg.svg"), 48% 68% / 18% no-repeat url("/images/pattern-quotes.svg");
}

.b-slide__header__container {
  display: grid;
  place-items: center;
}

.b-slide__image__container {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 80%;
  height: 80%;
}

.b-nav--bar {
  z-index: 1;
}

.b-button {
  border: none;
  padding: 1.5rem 1.5rem;
  position: relative;
  top: -15px;
}

.b-button:hover {
  cursor: pointer;
}

.b-button__left {
  border-top-left-radius: 50%;
  border-bottom-left-radius: 50%;
  background: 50% 50% / 28% no-repeat url("/src/assets/icon-prev.svg") white;
}

.b-button__right {
  border-top-right-radius: 50%;
  border-bottom-right-radius: 50%;
  background: 50% 50% / 31% no-repeat url("/src/assets/icon-next.svg") white;

}

.b-button__sign {
  max-width: 50%;
}
</style>