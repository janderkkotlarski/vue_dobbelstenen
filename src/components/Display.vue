<script setup>
import Dice from './Dice.vue';

const values = [6, 5, 4, 3, 2, 1, 2, 3, 4, 5, 6];
</script>

<template>
    <div class="row" v-for="value in values">
        <Dice :amount="value" />
    </div>
</template>
