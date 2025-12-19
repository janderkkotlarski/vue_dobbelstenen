<script setup>
// Just make the eyes in CSS and toggle the color with class declarations
const visibility = defineModel('visibility');
</script>

<template>
    <div class="eye" :class="visibility"></div>
</template>
