<script setup>
import Line from './Line.vue';

// const {amount = 0} = defineProps(['amount']);
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

const diceLine = diceLines[value];
</script>

<template>
    <div class="dice">
        <Line :selected="diceLine[0]" />
        <Line :selected="diceLine[1]" />
        <Line :selected="diceLine[2]" />
    </div>
</template>
