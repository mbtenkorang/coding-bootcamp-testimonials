<script setup>
import { ref } from 'vue';

const greet = ref("Hello World")
const testimonialdata = ref([{
  user_name: " John Tarkpor",
  user_role: "Junior Front-end Developer",
  "user_testimonial": " If you want to lay the best foundation possible I’d recommend taking this course.\
  The depth the instructors go into is incredible. I now feel so confident about \
  starting up as a professional developer. "
},
{
  user_name: "Tanya Sinclair",
  user_role: "UX Engineer",
  "user_testimonial": " I’ve been interested in coding for a while but never taken the jump, until now.\
  I couldn’t recommend this course enough. I’m now in the job of my dreams and so\
  excited about the future."
},])

</script>

<template>
  <h1>{{ greet }}</h1>
</template>

<style scoped></style>
