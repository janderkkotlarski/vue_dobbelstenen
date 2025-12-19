<script setup>
import Line from './Line.vue';

const value = defineModel('value');

const diceLines = [
    [0, 0, 0],
    [0, 2, 0],
    [1, 0, 3],
    [1, 2, 3],
    [4, 0, 4],
    [4, 2, 4],
    [4, 4, 4],
];
</script>

<template>
    <div class="dice">
        <Line v-for="i in 3" :selected="diceLines[value][i - 1]" />
    </div>
</template>
