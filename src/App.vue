<script setup>
import {ref} from 'vue';
import Dice from './components/Dice.vue';
import Eye from './components/Eye.vue';
import Line from './components/Line.vue';

const show = 'invisible';

const look = ref('visible');

// <Eye :visibility="look" />
</script>

<template>
    <Dice />
    <Dice />

    <Line />

    <Eye visibility="visible" />
    <br />
    <Eye :visibility="look" />
    <br />
</template>
