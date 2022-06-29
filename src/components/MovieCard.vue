<template>
    <div>
        <div>
            <img :src="`${baseUrl}${posterSize}${movie.poster_path}`" alt="">
        </div>

        <div>{{ movieTitle }}<span>
                <lang-flag :iso="movie.original_language" squared="false" />
            </span></div>
        <div>{{ movie.original_language }}</div>
        <div>{{ movie.vote_average }}</div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    data() {
        return {
            baseUrl: "https://image.tmdb.org/t/p/",
            posterSize: "w92",
        };
    },
    props: {
        movie: Object,

    },
    components: {
        LangFlag,
    },
    computed: {
        movieTitle() {
            if (this.movie.title) {
                return this.movie.title;
            } return this.movie.name;

        }
    },
}
</script>

<style>
</style>