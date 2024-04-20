<script setup>
const props = defineProps({
    imageurl: {
        type: String,
        required: true
    },
    username: {
        type: String,
        required: true
    }
})
</script>

<template>
    <img :src="imageurl" :alt="`Picture of ${username}`" class="profile-picture" />
</template>

<style>
.profile-picture {
    border-radius: 1rem;
    max-width: 90%;
}
</style>