<script setup>
import {useRoute} from 'vue-router'
import q from '../data/quizes.json'
import Question from '@/components/Question.vue';
import QuizHeader from '@/components/QuizHeader.vue';
import { ref,watch,computed } from 'vue';
import Result from '@/components/Result.vue';
const route=useRoute()

const quizId=parseInt(route.params.id)
const currentQuestionIndex=ref(0)
const numberOfCurrentAnswers=ref(0)
const quizCurrent=q.find(c=>c.id===quizId)
const showResults=ref(false)

// const questionStatus=ref(`${currentQuestionIndex.value}/${quizCurrent.questions.length}`)

// watch(()=>currentQuestionIndex.value,()=>{
//     questionStatus.value=`${currentQuestionIndex.value}/${quizCurrent.questions.length}`
// })
// instead of these two, we can use computed

const questionStatus=computed(()=>{
    return `${currentQuestionIndex.value}/${quizCurrent.questions.length}`
})

const barPercentage=computed(()=>`${currentQuestionIndex.value/quizCurrent.questions.length *100}%`)


const onOptionSelected=(isCorrect)=>{
    if(isCorrect){
        numberOfCurrentAnswers.value++
    }
    if(currentQuestionIndex.value==quizCurrent.questions.length-1){
        showResults.value=true
    }
    currentQuestionIndex.value++
}
</script>


<template>
    <div>
        <h1>Quiz View</h1>
        Quiz Name : {{ quizCurrent.name }}
        <hr>
        <hr>
    </div>
    <div>
        <QuizHeader 
            :questionStatus="questionStatus"
            :barPercentage="barPercentage"
        />
        <Question
            v-if="!showResults"
            :question="quizCurrent.questions[currentQuestionIndex]"
            @selectOption="onOptionSelected"
        />
        <Result
            v-else
            :quizQuestionLength="quizCurrent.questions.length"
            :numberOfCurrentAnswers="numberOfCurrentAnswers"
        />
    </div>
    <!-- <button @click="currentQuestionIndex++">Next Question</button> -->
</template>

