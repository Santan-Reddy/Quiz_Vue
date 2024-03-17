<script setup>
import {defineProps} from 'vue'
import {RouterLink} from 'vue-router'
const {quizQuestionLength,numberOfCurrentAnswers}=defineProps(['quizQuestionLength','numberOfCurrentAnswers'])
</script>

<template>
    <div>
        <h1>Your results are:</h1>
        <p>{{numberOfCurrentAnswers}}/{{quizQuestionLength}}</p>
    </div>
    <RouterLink to="/">Go to home</RouterLink>
</template>

<style scoped>
div{
    text-align: center;
}
h1{
    font-size: 2rem;
}
p{
    font-size: 3rem;
}
</style>