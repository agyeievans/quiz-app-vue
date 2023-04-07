<script setup>
import question from '../components/question.vue';
import quizheader from '../components/quizheader.vue';
import { useRoute } from 'vue-router';
import { ref } from 'vue';
import quizzes from "../data/quizzes.json"

const route = useRoute()

const quizId = parseInt(route.params.id)

const quiz = quizzes.find(q => q.id === quizId)

const currentQuestionIndex = ref(0)
</script>

<template>
    <div>
        <quizheader />
        <div>
            <question :question="quiz.questions[currentQuestionIndex]"/>
        </div>
    </div>
</template>
