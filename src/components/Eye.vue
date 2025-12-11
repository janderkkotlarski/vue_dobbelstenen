<script setup>
import {ref} from 'vue';

const props = defineProps(['visibility']);

const show = 'visible';
</script>

<template>
    <div :class="visibility"></div>
</template>
