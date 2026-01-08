<script setup>
import {reactive} from 'vue';
import Dice from './Dice.vue';

// Simple constants
const valueMax = 6;
const diceAmount = 8;

// reactive() for arrays and simpler handling
const diceValues = reactive([]);
const valueCounts = reactive([]);

// reactive() objects can just be passed along like variables
const reactArrayIndex = (reactName, index, amount) => {
    // Check whether generating or changing array contents
    if (index === reactName.length) {
        // Generate new array contents
        reactName.push({id: index + 1, entry: amount});
    } else {
        // Change specific array content
        reactName[index].entry = amount;
    }
};

// Simple dice roll function
const roll = () => Math.floor(valueMax * Math.random()) + 1;

// Roll a specific die
const diceRoll = index => {
    reactArrayIndex(diceValues, index, roll());
};

// Roll all dice, then update results
const rolling = () => {
    for (let i = 0; i < diceAmount; ++i) {
        diceRoll(i);
    }

    valueCounting();
};

const reroll = index => {
    diceRoll(index);

    // Update new result
    valueCounting();
};

// For each result count the number of dice showing that result
const valueCounting = () => {
    for (let index = 0; index < valueMax; ++index) {
        let count = 0;

        for (let jndex = 0; jndex < diceAmount; ++jndex) {
            if (diceValues[jndex].entry === index + 1) {
                ++count;
            }
        }

        reactArrayIndex(valueCounts, index, count);
    }
};

rolling();
</script>

<template>
    <div>
        <Dice @click="reroll(value.id - 1)" v-for="value in diceValues" :key="value.id" v-model:value="value.entry" />
    </div>

    <br />
    <button @click="rolling">Opnieuw rollen?</button>
    <br />

    <br />
    <table>
        <tr>
            <th>Waarde</th>
            <th>Hoeveelheid</th>
        </tr>
        <tr v-for="value in valueCounts" :key="value.id">
            <td>{{ value.id }}</td>
            <td>{{ value.entry }}</td>
        </tr>
    </table>
</template>
