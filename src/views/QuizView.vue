<script setup>
    import Question from '../components/Question.vue'
    import QuizHeader from '../components/QuizHeader.vue'
    import Result from '../components/Result.vue'
    import { computed, reactive, ref } from 'vue'
    import { useRoute } from 'vue-router'
    import quizzesData from '../data/quizzes.json'

    const route = useRoute()
    const quizId = parseInt(route.params.id)
    const currentQuestionIndex = ref(0)
    const quizzes = reactive(quizzesData)
    const numberOfCorrectAnswers = ref(0)
    const showResult = computed(() => currentQuestionIndex.value === quizzes.length)

    const quiz = computed(() => quizzes.find(quiz => quiz.id === quizId))

    const questionStatus = computed(() => {
        if (currentQuestionIndex.value >= quiz.value.questions.length){
            return `${currentQuestionIndex.value}/${quiz.value.questions.length}`
        }
        return `${currentQuestionIndex.value + 1}/${quiz.value.questions.length}`
    })

    const barCompletion = computed(() => `${currentQuestionIndex.value / quiz.value.questions.length * 100}%`)

    const onOptionSelected = (isCorrect) => {
        isCorrect ? numberOfCorrectAnswers.value++ : numberOfCorrectAnswers.value

        currentQuestionIndex.value++
    }
</script>

<template>
    <div>
        <QuizHeader :questionStatus="questionStatus" :barCompletion="barCompletion"/>
        <div>
            <Question :question="quiz.questions[currentQuestionIndex]" @selectOption="onOptionSelected" v-if="!showResult"/>
            <Result :numberOfCorrectAnswers="`${numberOfCorrectAnswers}/${quiz.questions.length}`" v-else/>
        </div>
    </div>
</template>

<style scoped>
</style>