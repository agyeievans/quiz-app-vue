<script setup>
    // import {defineProps} from "vue"

    const {questionStatus, barPercentage} = defineProps(["questionStatus", "barPercentage"])
</script>

<template>
    <header>
        <h1>Question {{questionStatus}}</h1>
        <div class="bar">
            <div class="completion" :style="{width: barPercentage}"></div>
        </div>
    </header>
</template>

<style scoped>
header {
    margin-top: 10px;
}

header h1 {
    font-size: 30px;
    margin-top: -10px;
}

.bar {
    width: 300px;
    height: 40px;
    border: 3px solid bisque;
}

.completion {
    height: 100%;
    width: 0%;
    background-color: bisque;
}

</style>