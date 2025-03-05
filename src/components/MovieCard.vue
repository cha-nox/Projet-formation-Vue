<script setup lang="ts">
defineProps<{ title: string, description: string, image_url: string }>();
</script>

<template>
    <article>
      <div class="image-container">
        <img :src="image_url" :alt="title">
        <div class="overlay">
          <h2>{{ title }}</h2>
          <hr>
          <p>{{ description.length > 320 ? description.slice(0, 300) + "[...]" : description }}</p>
        </div>
      </div>
    </article>
</template>

<style scoped>
article{
    background-color: rgba(70, 90, 126,  0.4);
    border-radius: 10px;
    padding: 10px;
}
img{
    width: 100%;
    height: auto;
    border-radius: 10px;
    display: block;
}
.overlay{
    position: absolute;
    top: 0;
    left: 0;
    width: calc(100% - 2 * 15px);
    height: calc(100% - 2 * 15px);
    background: rgba(0, 0, 0, 0.6);
    color: white;
    opacity: 0;
    transition: opacity 0.3s ease;
    padding: 15px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    border-radius: 10px;
}
.image-container{position: relative;}
.image-container:hover .overlay {opacity: 1;}
h2{
    font-size: 1.3em;
    margin: 0;
}
hr{
    border: 1px solid #fff;
    margin: 10px 0;
}
p{
    font-size: 1em;
    margin: 0;
}
</style>