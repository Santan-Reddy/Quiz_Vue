<script setup>
  import q from "./data/quizes.json"
  import {ref,watch} from 'vue'
  import Card from "./components/Card.vue"
  const quizes=ref(q)
  const search=ref("")

  watch(search,()=>{
    quizes.value=q.filter(quiz=>quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })
</script>

<template>
  <main>
    <header>
      <h1>Quizes</h1>
      <input v-model="search" type="text" placeholder="Search... ">
    </header>
    <div class="options-container">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz"/>
      <!-- <div class="card" v-for="quiz in quizes" :key="quiz.id">
        <img :src="quiz.img" alt="">
        <div class="card-text">
          <h2>{{quiz.name}}</h2>
          <p>{{quiz.questions.length}} questions</p>
        </div>
      </div> -->
    </div>
  </main>
</template>

<style scoped>
main{
  max-width: 1200px;
  margin: 0 auto;
}
header{
  display: flex;
  align-items: center;
  margin: 20px 0 40px;
}
header h1{
  font-weight: bold;
  font-size: 2rem;
  margin-right: 1rem;
}
header input{
  border: none;
  outline: none;
  border-radius: 5px;
  background-color: rgb(208, 234, 245);
  padding: 1rem;
}
.options-container{
  margin-top: 40px;
  display: flex;
  flex-wrap: wrap;
}
/* card */
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