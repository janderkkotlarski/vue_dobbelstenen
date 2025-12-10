<script setup>
import {ref} from 'vue';
import Eye from './Eye.vue';
const amount = ref(-1);
const space = ref(' ');

const line = ref('<Eye \/>space<Eye \/>{{ space }}<Eye \/><br \/>');
</script>

<template>
    <Eye />
    {{ space }}
    <Eye />
    {{ space }}
    <Eye />
    <br />

    <Eye />
    {{ space }}
    <Eye />
    {{ space }}
    <Eye />
    <br />

    <Eye />
    {{ space }}
    <Eye />
    {{ space }}
    <Eye />
    <br />

    <div :value="line"></div>
</template>
