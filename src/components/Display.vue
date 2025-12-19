<script setup>
import {ref} from 'vue';
import Dice from './Dice.vue';

const diceAmount = 8;

const roll = () => Math.floor(6 * Math.random()) + 1;

const rolling = () => {
    let values = [];

    for (let i = 0; i < diceAmount; ++i) {
        values.push(roll());
    }

    return values;
};

const diceValues = ref(rolling());

const reroll = index => {
    // With ref, the value is the array on to which to apply the index.
    diceValues.value[index] = roll();
};

const rerolling = () => {
    for (let index = 0; index < diceAmount; ++index) {
        reroll(index);
    }
};
</script>

<template>
    <div class="row">
        <Dice @click="reroll(index - 1)" v-for="index in diceAmount" v-model:value="diceValues[index - 1]" />
    </div>

    <button @click="rerolling">Opnieuw rollen?</button>
</template>
