<script setup>
import Eye from './Eye.vue';

// No fussing with extraneous ref variables, those break the simple functioning
const selected = defineModel('selected', {type: Number, default: 4});

const eyeLines = [
    ['invis', 'invis', 'invis'],
    ['visible', 'invis', 'invis'],
    ['invis', 'visible', 'invis'],
    ['invis', 'invis', 'visible'],
    ['visible', 'invis', 'visible'],
];
</script>

<template>
    <div>
        <Eye v-for="i in 3" :visibility="eyeLines[selected][i - 1]" />
    </div>
</template>
