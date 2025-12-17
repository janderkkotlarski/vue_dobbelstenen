<script setup>
import {ref, reactive} from 'vue';
import Dice from './Dice.vue';

let roll = () => Math.floor(6 * Math.random()) + 1;

let rolling = amount => {
    let diceValues = [];

    for (let i = 0; i < amount; ++i) {
        diceValues.push(roll());
    }

    return diceValues;
};

let state = reactive({values: []});

const reroll = () => {
    state.values = rolling(7);
};

const sharedValue = ref(0);

// reroll();
</script>

<template>
    <div class="row" v-for="value in state.values">
        <Dice v-model:value="sharedValue" />
    </div>

    <button @click="reroll">Herwerpen</button>
</template>
