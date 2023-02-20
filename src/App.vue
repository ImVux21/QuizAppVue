<script setup>
    import { RouterView } from 'vue-router'
</script>

<template>
    <div class="container">
        <RouterView />
    </div>
</template>

<style>
    .container {
        padding: 10px;
        height: 100vh;
        display: flex;
        margin-left: 50px;
        flex-direction: column;
    }
</style>