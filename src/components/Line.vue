<script setup>
import {ref} from 'vue';
import Eye from './Eye.vue';

// const {selected = 0} = defineProps(['selected']);

const selected = defineModel('selected', {type: Number, default: 4});

const eyeLines = [
    ['invis', 'invis', 'invis'],
    ['visible', 'invis', 'invis'],
    ['invis', 'visible', 'invis'],
    ['invis', 'invis', 'visible'],
    ['visible', 'invis', 'visible'],
];

/*
const updateLine = () => {
    // eyeLine.value = eyeLines[select.value];
};

updateLine();
*/

// const eyeLine = eyeLines[selected];

/*

    */
</script>

<template>
    <div>
        <Eye :visibility="eyeLines[selected][0]" />
        <Eye :visibility="eyeLines[selected][1]" />
        <Eye :visibility="eyeLines[selected][2]" />
    </div>
</template>
