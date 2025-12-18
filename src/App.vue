<script setup>
import {reactive} from 'vue';
import Display from './components/Display.vue';
import Eye from './components/Eye.vue';

const state = reactive({visibilityFeedback: 'visible'});
/*
<Display />

<button @click="flipper">{{ state.visibilityFeedback }}</button>
*/

const flipper = () => {
    if (state.visibilityFeedback) {
        state.visibilityFeedback = '';
    } else {
        state.visibilityFeedback = 'visible';
    }
};
</script>

<template>
    <Eye @click="flipper" v-model:visibility="state.visibilityFeedback" />
</template>
