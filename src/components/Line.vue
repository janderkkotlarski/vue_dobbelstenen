<script setup>
import {ref} from 'vue';
import Eye from './Eye.vue';
const space = ref(' ');

const eyeLines = [
    [0, 0, 0],
    [1, 0, 0],
    [0, 1, 0],
    [0, 0, 1],
    [1, 0, 0],
];

const eyeLine = ref(eyeLines[0]);

function makeVisible(line) {
    const visibles = [];

    for (let i = 0; i < line.length; ++i) {
        visibles.push(line[0] ? 'visible' : '');
    }

    return visibles;
}

const visibilityLine = makeVisible(eyeLine);

const eyeOn = document.createElement('Eye');
</script>

<template>
    <Eye />
    {{ space }}
    <Eye />
    {{ space }}
    <Eye />
    <br />
    {{ eyeOn }}
</template>
