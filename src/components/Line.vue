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
</script>

<template>
    <Eye />
    {{ space }}
    <Eye />
    {{ space }}
    <Eye />
    <br />
</template>
