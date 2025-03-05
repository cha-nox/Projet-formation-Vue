<script setup lang="ts">
    defineProps<{ label: string }>();
</script>

<template>
    <button type="submit">{{ label }}</button>
</template>

<style scoped></style>