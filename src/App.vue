<script setup>
import {ref} from 'vue';
import Display from './components/Display.vue';
import Eye from './components/Eye.vue';
import Line from './components/Line.vue';
import Dice from './components/Dice.vue';

const visibilityFeedback = ref('visible');

const selectedMax = 4;
const selectedFeedback = ref(0);

const valueMax = 6;
const valueFeedback = ref(0);

const flipper = () => {
    if (visibilityFeedback.value === 'visible') {
        visibilityFeedback.value = 'invis';
    } else {
        visibilityFeedback.value = 'visible';
    }
};

const switcher = () => {
    if (selectedFeedback.value < selectedMax) {
        ++selectedFeedback.value;
    } else {
        selectedFeedback.value = 0;
    }
};

const changer = () => {
    if (valueFeedback.value < valueMax) {
        ++valueFeedback.value;
    } else {
        valueFeedback.value = 0;
    }
};

/*
<Display />

<Eye @click="flipper" v-model:visibility="visibilityFeedback" />

<Line @click="switcher" v-model:selected="selectedFeedback" />
*/
</script>

<template>
    <Dice @click="changer" v-model:value="valueFeedback" />
</template>
