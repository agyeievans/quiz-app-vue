<script setup>
import question from '../components/question.vue';
import quizheader from '../components/quizheader.vue';
import result from '../components/result.vue';
import { useRoute } from 'vue-router';
import { ref, watch, computed } from 'vue';
import quizzes from "../data/quizzes.json"

const route = useRoute()

const quizId = parseInt(route.params.id)

const quiz = quizzes.find(q => q.id === quizId)

const currentQuestionIndex = ref(0)

const numberOfCorrectAnswers = ref(0)

const showResults = ref(false)

// const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

// watch(() => currentQuestionIndex.value, () => {
//     questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`
// })

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barPercentage = computed(() => `${currentQuestionIndex.value/quiz.questions.length *100}%`)

const onOptionSelected = (isCorrect) => {
    if(isCorrect){
        numberOfCorrectAnswers.value++;
    }

    if(quiz.questions.length -1 === currentQuestionIndex.value){
        showResults.value = true
    }

    currentQuestionIndex.value++
}

</script>

<template>
    <div>
        <quizheader :questionStatus="questionStatus" :barPercentage="barPercentage" />
        <div>
            <question v-if="!showResults" :question="quiz.questions[currentQuestionIndex]" 
            @selectOption="onOptionSelected" />

            <result v-else 
            :quizQuestionLength="quiz.questions.length"
            :numberOfCorrectAnswers="numberOfCorrectAnswers" />
        </div>
    </div>
</template>
