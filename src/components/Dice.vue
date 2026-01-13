<script setup>
import Line from './Line.vue';

// Default is for empty die
const value = defineModel('value', {type: Number, default: 0});

// Possible dice line configs
const diceLines = [
    [0, 0, 0], // 0
    [0, 2, 0], // 1
    [1, 0, 3], // 2
    [1, 2, 3], // 3
    [4, 0, 4], // 4
    [4, 2, 4], // 5
    [4, 4, 4], // 6
];
</script>

<template>
    <div class="dice">
        <Line v-for="i in 3" :selected="diceLines[value][i - 1]" />
    </div>
</template>
