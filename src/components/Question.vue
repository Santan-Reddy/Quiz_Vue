<script setup >
import { defineProps,defineEmits } from 'vue';
const emit=defineEmits(['selectOption'])
const {question}=defineProps(['question'])

const emitSelectedOption=(isCorrect)=>{
    emit('selectOption',isCorrect)
}
</script>

<template>
    <div>
        <div class="question-container">
            <h1 class="question">
                {{question.text}}
            </h1>
        </div>
        <div class="option-container">
            <div class="option" v-for="option in question.options" :key="option.id" @click="emitSelectedOption(option.isCorrect)">
                <p class="option-label">{{option.label}}</p>
                <p class="option-value">{{option.text}}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
.question-container{
    margin-top: 1.5rem;

}
.option{
    margin-top: 1.2rem;
    display: flex;
    font-size: 1.4rem;
    align-items: center;
    cursor: pointer;
}
.option-label{
    background-color: rgb(241, 161, 56);
    padding: 1rem;
}
.option-value{
    width: 100%;
    background-color: antiquewhite;
    padding: 1rem;
}
</style>