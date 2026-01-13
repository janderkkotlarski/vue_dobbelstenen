<script setup>
import Line from './Line.vue';

// Default is for empty die
const value = defineModel('value', {type: Number, default: 0});

// Possible dice line configs
// const diceLines = [
//     {id: 0, lines: [0, 0, 0]},
//     {lines: [0, 2, 0]}, // 1
//     {lines: [1, 0, 3]}, // 2
//     {lines: [1, 2, 3]}, // 3
//     {lines: [4, 0, 4]}, // 4
//     {lines: [4, 2, 4]}, // 5
//     {lines: [4, 4, 4]}, // 6
// ];

const diceLines = [
    {id: 1, lines: [0, 0, 1, 1, 4, 4, 4]},
    {id: 2, lines: [0, 2, 0, 2, 0, 2, 4]},
    {id: 3, lines: [0, 0, 3, 3, 4, 4, 4]},
];

// <Line v-for="diceLine in diceLines" :key="diceLine.id" :selected="diceLine.lines[value]" />
</script>

<template>
    <div class="dice">
        <Line v-for="diceLine in diceLines" :key="diceLine.id" :selected="diceLine.lines[value]" />
    </div>
</template>
