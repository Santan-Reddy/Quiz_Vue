<script setup>
import {defineProps} from 'vue'

const {questionStatus,barPercentage}=defineProps(['questionStatus','barPercentage'])
</script>


<template>
    <header>        
        <h3>Question {{ questionStatus }}</h3>
        <div class="bar">
            <div class="completion" :style="{width:barPercentage}"></div>
        </div>
    </header>
</template>
<style scoped>
header{
    margin-top: 20px;
}
header h3{
    font-size: 3rem;
}
.bar{
    border: 3px solid rgb(255, 203, 107);
    height: 2rem;
    width: 20rem;
}
.completion{
    height: 100%;
    width: 0%;
    background-color: orange;
}

</style>