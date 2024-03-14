<script setup>
import {defineProps} from 'vue'

const {quiz}=defineProps(['quiz'])
</script>

<template>
    <div class="card">
        <img :src="quiz.img" alt="img">
        <div class="card-text">
          <h2>{{quiz.name}}</h2>
          <p>{{quiz.questions.length}} questions</p>
        </div>
      </div>
</template>

<style scoped>
.card{
  width: 320px;
  border-radius: 5px;
  margin: 1rem 1rem;
  /* overflow: hidden; */
  cursor: pointer;
  background-color: rgb(145, 220, 167);
}
.card img{
  height: 200px;
  width: 100%;
  border-radius: 5px 5px 0 0;
  object-fit: cover;
}
.card .card-text{
  padding:  5px;
}
.card .card-text h2{
  font-weight: bold;
}
</style>