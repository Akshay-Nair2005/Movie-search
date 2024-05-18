<template>
    <div class="app">
        <h1>MoviesMania</h1>

        <div class="search">
            <input v-model="searchTerm" placeholder="Search for movies" />
            <img src="@/assets/search.svg" alt="search" @click="searchMovies(searchTerm)" />
        </div>
        <div v-if="movies.length > 0" class="container">
            <MovieCard v-for="(movie, index) in movies" :key="index" :movie="movie" />
        </div>
        <div v-else class="empty">
            <h2>No movies found</h2>
        </div>
    </div>
</template>

<script>
import MovieCard from "../components/MovieCard.vue";
import '~/assets/css/index.css';

const API_URL = "http://www.omdbapi.com?apikey=5d16fbef";

export default {
    name: "App",
    components: {
        MovieCard,
    },
    data() {
        return {
            searchTerm: "",
            movies: [],
        };
    },
    mounted() {
        this.searchMovies("Batman");
        this.searchTerm = "Batman";
    },
    methods: {
        async searchMovies(searchTerm) {
            const response = await fetch(`${API_URL}&s=${searchTerm}`);
            const data = await response.json();
            this.movies = data.Search || [];
        },
    },
};
</script>

<style></style>