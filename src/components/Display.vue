<script setup>
import {ref} from 'vue';
import Dice from './Dice.vue';

const valueMax = 6;

const diceAmount = 8;

const roll = () => Math.floor(valueMax * Math.random()) + 1;

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

const valueCountInit = () => {
    let counts = [];

    for (let i = 0; i < valueMax; ++i) {
        counts.push({diceValue: i + 1, rollCount: 0});
    }

    return counts;
};

// const valueCounts = ref(valueCountInit());

const valueRecount = () => {
    let counts = [];

    for (let i = 0; i < valueMax; ++i) {
        let count = 0;

        for (let j = 0; j < diceAmount; ++j) {
            if (diceValues.value[j] === i + 1) {
                ++count;
            }
        }

        counts.push({diceValue: i + 1, rollCount: count});
    }

    return counts;
};

const valueCounts = ref(valueRecount());
</script>

<template>
    <div>
        <Dice @click="reroll(index - 1)" v-for="index in diceAmount" v-model:value="diceValues[index - 1]" />
    </div>
    <br />
    <button @click="rerolling">Opnieuw rollen?</button>
    <br />
    <table>
        <tr>
            <th>Waarde</th>
            <th>Hoeveelheid</th>
        </tr>
        <tr v-for="value in valueCounts">
            <td>{{ value.diceValue }}</td>
            <td>{{ value.rollCount }}</td>
        </tr>
    </table>
</template>
