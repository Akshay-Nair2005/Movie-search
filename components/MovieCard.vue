<template>
    <div class="movie">
        <div>
            <p>{{ movie.Year }}</p>
        </div>
        <div>
            <img :src="movie.Poster !== 'N/A' ? movie.Poster : 'https://via.placeholder.com/400'" :alt="movie.Title" />
        </div>
        <div>
            <span>{{ movie.Type }}</span>
            <h3>{{ movie.Title }}</h3>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        movie: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
/* .movie {
    border: 1px solid #ccc;
    padding: 20px;
    margin: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.movie img {
    max-width: 200px;
    height: auto;
    margin-bottom: 10px;
} */
</style>