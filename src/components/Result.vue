<script setup>
    import { defineProps } from 'vue'
    import { RouterLink } from 'vue-router'

    const { numberOfCorrectAnswers } = defineProps(['numberOfCorrectAnswers'])
</script>

<template>
    <div class="results">
        <p>Your Results...</p>
        <h1>{{ numberOfCorrectAnswers }}</h1>
        <RouterLink to="/">Back to Home</RouterLink>
    </div>
</template>

<style scoped>
    .results {
        text-align: center;
        padding: 100px 0;
    }

    .results p {
        font-size: 30px;
        margin-bottom: 20px;
    }

    h1 {
        font-size: 50px;
    }
</style>