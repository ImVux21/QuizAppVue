<script setup>
    import { defineProps } from 'vue'

    const { questionStatus, barCompletion } = defineProps(['questionStatus', 'barCompletion'])
</script>

<template>
    <header>
        <h4>Question {{ questionStatus }}</h4>
        <div class="bar">
            <div class="completion" :style="{width: barCompletion}"></div>
        </div>
    </header>
</template>

<style scoped>
    header {
        margin-top: 30px;
    }

    header h4 {
        font-size: 30px;
    }

    .bar {
        width: 300px;
        height: 50px;
        background-color: #e0e0e0;
        border-radius: 5px;
        margin-top: 10px;
    }

    .completion {
        width: 0;
        height: 100%;
        background-color: #00bfa5;
        border-radius: 5px;
    }
</style>