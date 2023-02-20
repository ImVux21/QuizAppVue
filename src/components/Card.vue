<script setup>
    import { defineProps } from 'vue'
    import { useRouter } from 'vue-router'

    const router = useRouter()
    const { quiz } = defineProps(['quiz'])
    
    const navigateQuiz = () => {
        router.push(`/quiz/${quiz.id}`)
    }
</script>

<template>
    <div class="card" @click="navigateQuiz">
        <img :src="quiz.img" alt="">
        <div class="card-text">
            <h2>{{ quiz.name }}</h2>
            <p>{{ quiz.questions.length }} questions</p>
        </div>
    </div>
</template>

<style scoped>
    .card {
        background-color: aliceblue;
        color: black;
        width: 310px;
        overflow: hidden;
        border-radius: 5px;
        box-shadow: 1px 1px 10px rgba(226, 223, 223, 0.522);
        margin-bottom: 35px;
        margin-right: 20px;
        cursor: pointer;
    }

    .card img {
        height: 200px;
        margin: 0;
        object-fit: cover;
    }

    .card .card-text {
        padding: 0 5px;
    }

    .card .card-text h2 {
        font-weight: bold;
        margin: 0;
        margin-top: 10px;
    }
</style>