<script setup>
import {ref} from 'vue';
import Eye from './Eye.vue';
const space = ref(' ');

const eyeLines = [
    ['', '', ''],
    ['visible', '', ''],
    ['', 'visible', ''],
    ['', '', 'visible'],
    ['visible', '', 'visible'],
];

const eyeLine = ref(eyeLines[4]);
</script>

<template>
    <Eye :visibility="eyeLine[0]" />
    {{ space }}
    <Eye :visibility="eyeLine[1]" />
    {{ space }}
    <Eye :visibility="eyeLine[2]" />
    <br />
</template>
