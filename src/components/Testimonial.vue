<script setup>
const props = defineProps({
    usertestimonial: {
        type: String,
        required: true

    },
    username: {
        type: String,
        default: "Unknown"

    },
    userrole: {
        type: String,
        default: "Unknown"

    },
})
</script>

<template>
    <div class="b-slide__testimonial__container">
        <div class="b-slide__footer">
            <h1 class="b-slide__username">{{ username }}</h1>
            <p class="b-slide__userrole">{{ userrole }}</p>
        </div>
        <p class="b-slide__text">" {{ usertestimonial }} "</p>
    </div>
</template>
