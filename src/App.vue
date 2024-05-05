<script setup>
import { ref, computed, Transition } from 'vue';
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

  <article class="b-slide__main__container" :key="currentSlideIndex">
    <!-- Testimonial Image -->
    <div class="b-slide__header__container">
      <div class="b-slide__image__container">
        <ProfileImage :imageurl="currentSlide.imageurl" :username="currentSlide.username" />
        <!-- Navigation Buttons -->
        <div class="b-nav--bar">
          <button role="button" @click="previousSlide" aria-labelledby="previous testimonial" aria-label="Previous Testimonial" Title="Previous Testimonial" class="b-button b-button__left">
          </button>

          <button role="button" @click="nextSlide" aria-labelledby="next testimonial" aria-label="Next Testimonial" Title="Next Testimonial" class="b-button b-button__right">
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
  background: 42% top / 92% no-repeat url("/images/pattern-bg.svg"), 50% 61% / 15% no-repeat url("/images/pattern-quotes.svg");
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

.profile-picture {
  border-radius: 1rem;
  max-width: 90%;
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

.b-slide__testimonial__container {
  display: flex;
  flex-direction: column-reverse;
  align-items: center;
  justify-content: center;
}

.b-slide__footer {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.b-slide__username {
  color: var(--darkblue);
  font-weight: 700;
  font-size: 1rem;
  margin-block-end: .25em;
}

.b-slide__userrole {
  color: var(--grayishblue);
}

.b-slide__text {
  text-align: center;
  font-weight: 300;
  font-size: 1.2rem;
  line-height: 1.3;
  margin-block-end: 1.25em;
  color: var(--darkblue);
  width: 80%;
}

/* Animation Settings */
.profile-picture, .b-slide__testimonial__container{
  animation: 3s ease-in backwards showElement;
}

@keyframes showElement{
    0%{
        opacity: 0;
        transform: translateX(30px);
    }
    100%{
        opacity: 1;
        transform: scale(1);
    }
}

@keyframes exitElement{

}


/* Media Query for Tablets */
@media only screen and (min-width: 499px) and (max-width: 800px){
  
  .b-container{
    max-width: 30rem;
    margin-inline: auto;
  }
}


/* Media Query for Desktop */
@media only screen and (min-width: 890px) {
  .b-container {
    background-size: 40%;
    max-width: 96%;
    background-size: 50%;
  }

  .b-slide__main__container {
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 1fr;
    grid-template-areas: "t i";
    background-position: right, left 22% top 22%;
    background-size: contain, 8%;
    min-height: 40rem;
  }

  .b-slide__header__container {
    grid-area: i;
    justify-items: center;
  }

  .profile-picture {
    max-width: 100%;
    position: relative;
    top: -2%;
  }

  .b-button {
    right: 150%;
    top: -65%;
  }

  .b-slide__testimonial__container {
    grid-area: t;
    align-items: flex-start;
    justify-content: center;
    position: relative;
    left: 22%;
    margin-inline-start: 2.5em;
  }

  .b-slide__footer {
    flex-direction: row;
    align-items: baseline;
  }

  .b-slide__username {
    margin-inline-end: 1rem;
  }

  .b-slide__text {
    font-size: 2rem;
    max-width: 100%;
    text-align: left;
    width: 100%;
  }
}
</style>