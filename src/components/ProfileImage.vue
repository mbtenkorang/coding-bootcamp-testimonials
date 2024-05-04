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
