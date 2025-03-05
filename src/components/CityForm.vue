<script setup lang="ts">
    import { ref } from 'vue';
    import axios from 'axios';
    import CityInput from './CityInput.vue';
    import SubmitButton from './SubmitButton.vue';
    import MovieCard from './MovieCard.vue';

    const city_name = ref('');
    let movies : any = ref(null);

    function updateCity(event: Event){
        const input = event.target as HTMLInputElement;
        city_name.value = input.value;
    };

    async function submitForm(){
        try{
            const movies_data = await axios.get(import.meta.env.VITE_BACKEND_URL + '/movies/recommendation?city_name=' + city_name.value);
            movies.value = movies_data.data[0].results;
        }
        catch(error){
            console.error("Erreur lors de l’appel à l’API : ", error)
        };
    };
</script>

<template>
    <form @submit.prevent="submitForm">
        <CityInput placeholder="Entrez le nom de la ville" @input="updateCity"/>
        <hr>
        <SubmitButton label="Envoyer"/>
        <br><br><br>
        <section>
            <MovieCard v-for="movie in movies" :key="movie.id" :title="movie.title" :description="movie.overview" :image_url="'https://image.tmdb.org/t/p/original/' + movie.poster_path"/>
        </section>
    </form>
</template>

<style scoped>
section{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 30px 20px;
}
</style>