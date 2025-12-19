<script setup>
import {ref} from 'vue';
import Display from './components/Display.vue';
import Eye from './components/Eye.vue';
import Line from './components/Line.vue';
import Dice from './components/Dice.vue';

const valueMax = 6;
const valueFeedback = ref(0);

const changer = () => {
    if (valueFeedback.value < valueMax) {
        ++valueFeedback.value;
    } else {
        valueFeedback.value = 0;
    }
};

/*

<Dice @click="changer" v-model:value="valueFeedback" />

<Dice @click="changer" v-model:value="valueFeedback" />
*/
</script>

<template>
    <Display />
</template>
