<script setup>
import {ref} from 'vue';
import Eye from './Eye.vue';
const space = ref(' ');

const {selected = 0} = defineProps(['selected']);

const eyeLines = [
    ['', '', ''],
    ['visible', '', ''],
    ['', 'visible', ''],
    ['', '', 'visible'],
    ['visible', '', 'visible'],
];

const eyeLine = eyeLines[selected];
</script>

<template>
    <div>
        <Eye :visibility="eyeLine[0]" />
        <Eye :visibility="eyeLine[1]" />
        <Eye :visibility="eyeLine[2]" />
    </div>
</template>
