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
    <div class="b-slide__testimonial">
        <div class="b-slide__footer">
            <h1 class="b-slide__username">{{ username }}</h1>
            <p class="b-slide__userrole">{{ userrole }}</p>
        </div>
        <p class="b-slide__text">" {{ usertestimonial }} "</p>
    </div>
</template>

<style>
.b-slide__testimonial {
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    justify-content: flex-start;
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

}

.b-slide__userrole {
    color: var(--grayishblue);
}

.b-slide__text {
    text-align: center;
    font-weight: 300;
    font-size: 1.1rem;
    margin-block-end: 1.5rem;
    color: var(--darkblue);
    max-width: 94%;
}
</style>