<script setup lang="ts">
    defineProps<{ placeholder: string }>();
</script>

<template>
    <input type="text" name="city_name" id="city_name" :placeholder="placeholder"/>
</template>

<style scoped>
input{
    border: none;
    border-radius: 8px;
    width: 300px;
    height: 30px;
    padding: 5px;
    font-size: 16px;
}
</style>