<script setup>
const {visibility = ''} = defineProps(['visibility']);
</script>

<template>
    <div class="eye" :class="visibility"></div>
</template>
