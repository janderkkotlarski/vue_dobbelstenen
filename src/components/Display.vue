<script setup>
import {ref} from 'vue';
import Dice from './Dice.vue';

const valueMax = 6;

const diceAmount = 8;

const valueCounts = ref([]);

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

    // Recalculate dice value counts
    valueCounting();
};

const rerolling = () => {
    for (let index = 0; index < diceAmount; ++index) {
        reroll(index);
    }
};

const valueCounting = () => {
    // .value is the key to correct ref usage
    // This works like a charm, even for empty arrays
    // Just start at index 0
    for (let i = 0; i < valueMax; ++i) {
        let count = 0;

        for (let j = 0; j < diceAmount; ++j) {
            if (diceValues.value[j] === i + 1) {
                ++count;
            }
        }

        valueCounts.value[i] = {diceValue: i + 1, rollCount: count};
    }
};

valueCounting();
</script>

<template>
    <div>
        <Dice @click="reroll(index - 1)" v-for="index in diceAmount" v-model:value="diceValues[index - 1]" />
    </div>
    <br />
    <button @click="rerolling">Opnieuw rollen?</button>
    <br />
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
