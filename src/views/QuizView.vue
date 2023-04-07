<script setup>
import question from '../components/question.vue';
import quizheader from '../components/quizheader.vue';
import { useRoute } from 'vue-router';
import { ref, watch, computed } from 'vue';
import quizzes from "../data/quizzes.json"

const route = useRoute()

const quizId = parseInt(route.params.id)

const quiz = quizzes.find(q => q.id === quizId)

const currentQuestionIndex = ref(0)

// const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

// watch(() => currentQuestionIndex.value, () => {
//     questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`
// })

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barPercentage = computed(() => `${currentQuestionIndex.value/quiz.questions.length *100}%`)

</script>

<template>
    <div>
        <quizheader :questionStatus="questionStatus" :barPercentage="barPercentage" />
        <div>
            <question :question="quiz.questions[currentQuestionIndex]" />
        </div>
        <button @click="currentQuestionIndex++">Next Question</button>
    </div>
</template>
