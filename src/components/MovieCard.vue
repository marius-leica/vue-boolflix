<template>
    <div>

        <div>{{ movie.title }} <span>
                <lang-flag :iso="movie.original_language" squared="false" />
            </span></div>
        <div>{{ movie.original_title }}</div>
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
}
</script>

<style>
</style>