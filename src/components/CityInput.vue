<script setup lang="ts">
    defineProps<{ placeholder: string }>();
</script>

<template>
    <input type="text" name="city_name" id="city_name" :placeholder="placeholder"/>
</template>

<style scoped></style>