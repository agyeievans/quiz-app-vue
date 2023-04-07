<script setup>
    import {RouterLink} from "vue-router"

    const {quizQuestionLength, numberOfCorrectAnswers} = defineProps(["quizQuestionLength","numberOfCorrectAnswers"])
</script>

<template>
    <div class="result">
        <p>Your Result....</p>
        <h1> {{ numberOfCorrectAnswers }} / {{quizQuestionLength}}</h1>

        <router-link to="/">Go Back</router-link>
    </div>
</template>

<style scoped>
    .result{
        text-align: center;
        padding: 100px 0;
    }

    p{
        font-size: 20px;
    }

    h1{
        font-size: 80px;
    }
</style>