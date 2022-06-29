<template>
    <div>

        <div>{{ movie.title }} <span>
                <lang-flag :iso="movie.original_language" squared="false" />
            </span></div>
        <div>{{ movieTitle }}</div>
        <div>{{ movie.original_language }}</div>
        <div>{{ movie.vote_average }}</div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    props: {
        movie: Object,

    },
    components: {
        LangFlag,
    },
    computed: {
        movieTitle(movie) {
            if (movie.title) {
                return movie.title;
            } return movie.name;

        }
    },
}
</script>

<style>
</style>