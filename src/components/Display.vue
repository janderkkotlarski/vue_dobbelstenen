<script setup>
import {ref} from 'vue';
import Dice from './Dice.vue';

const valueMax = 6;

const diceAmount = 8;

let clicked = 0;

const diceValues = ref([]);

const valueCounts = ref([]);

const roll = () => Math.floor(valueMax * Math.random()) + 1;

const diceRoll = index => {
    // With ref, the value is the array on to which to apply the index.

    if (index === diceValues.value.length) {
        diceValues.value[index] = {diceIndex: index + 1, diceRoll: roll()};
    } else {
        diceValues.value[index].diceRoll = roll();

        ++clicked;
    }
};

const rolling = () => {
    for (let i = 0; i < diceAmount; ++i) {
        diceRoll(i);
    }

    valueCounting();
};

const reroll = index => {
    diceRoll(index);

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
            if (diceValues.value[j].diceRoll === i + 1) {
                ++count;
            }
        }

        if (i === valueCounts.value.length) {
            valueCounts.value[i] = {diceValue: i + 1, rollCount: count};
        } else {
            valueCounts.value[i].rollCount = count;
        }
    }
};

rolling();
</script>

<template>
    <div>
        <Dice @click="reroll(value.diceIndex - 1)" v-for="value in diceValues" v-model:value="value.diceRoll" />
    </div>

    <br />
    <button @click="rerolling">Opnieuw rollen?</button>
    <br />
    <div>{{ clicked }}</div>
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
