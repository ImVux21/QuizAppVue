<script setup>
    import { defineProps, defineEmits } from 'vue'

    const emit = defineEmits(['selectOption'])
    const { question } = defineProps(['question'])
    const emitSelectedoption = (isCorrect) => {
        emit('selectOption', isCorrect)
    }
</script>

<template>
    <div class="question-container">
        <h1 class="question">
            {{ question.text }}
        </h1>
    </div>
    <div class="options-container">
        <div class="option" v-for="option in question.options" :key="option.id" @click="emitSelectedoption(option.isCorrect)">
            <p class="option-label"> {{ option.label }}</p>
            <div class="option-value">
                <p>{{ option.text }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .question-container {
        margin-top: 30px;
    }

    .question {
        font-size: 40px;
        margin-bottom: 20px;
    }

    .option {
        display: flex;
        align-items: center;
        margin-bottom: 20px;
        cursor: pointer;
    }

    .option-label {
        color: black;
        background-color: bisque;
        width: 60px;
        height: 60px;
        font-size: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .option-value {
        color: black;
        margin-left: 20px;
        background-color: #e0e0e0;
        width: 100%;
        height: 60px;
        border-radius: 5px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

</style>