<script setup>
    import quizzesData from '../data/quizzes.json'
    import Card from '../components/Card.vue'
    import { reactive, ref, watch, defineProps } from 'vue'

    let quizzes = reactive(quizzesData)
    const search = ref('')

    watch(search, (value) => quizzes = quizzesData.filter((quiz) => quiz.name.toLowerCase().includes(value.toLowerCase())))
</script>

<template>
    <header>
        <h1>Quizzes</h1>
        <input v-model.trim="search" type="text" name="" id="" placeholder="Search...">
    </header>
    <div class="options-container">
        <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz"/>
    </div>
</template>

<style scoped>
    header {
        margin-bottom: 10px;
        margin-top: 30px;
        display: flex;
        align-items: center;
    }

    header h1 {
        font-weight: bold;
        margin-right: 30px;
    }

    header input {
        width: 300px;
        height: 30px;
        border: none;
        border-radius: 5px;
        padding: 10px;
        border-radius: 5px;
    }

    .options-container {
        display: flex;
        flex-wrap: wrap;
        margin-top: 40px;
    }
</style>