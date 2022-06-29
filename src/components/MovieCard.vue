<template>
    <div>
        <div>
            <img :src="`${baseUrl}${posterSize}${movie.poster_path}`" alt="">
        </div>

        <div>{{ movieTitle }}<span>
                <lang-flag :iso="movie.original_language" squared="false" />
            </span></div>
        <div>{{ movie.original_language }}</div>
        <div>{{ starGaverate }}</div>
        <div v-if="starGaverate === 1">
            <i class="fa-solid fa-star"></i>
        </div>
        <div v-if="starGaverate === 2">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
        </div>
        <div v-if="starGaverate === 3">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
        </div>
        <div v-if="starGaverate === 4">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
        </div>
        <div v-if="starGaverate === 5">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
        </div>

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

        },
        starGaverate() {
            return Math.round(this.movie.vote_average / 2);
        },
    },
    methods: {

    },
}
</script>

<style lang="scss" scoped>
.fa-solid {
    color: #ffc107;
}
</style>