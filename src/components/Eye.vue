<script setup>
// const {visibility = ''} = defineProps(['visibility']);

const visibility = defineModel('visibility');
</script>

<template>
    <div class="eye" :class="visibility"></div>
</template>
