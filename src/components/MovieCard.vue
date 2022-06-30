<template>

    <div class="card h-100 position-relative">

        <img :src="imageControl" alt="">
        <div class="card-absolute">
            <div><strong>Titolo:</strong>{{ " " + movieTitle }}<span>
                    <lang-flag :iso="movie.original_language" />
                </span>
            </div>
            <div><strong>Titolo originale:</strong> {{ " " + originalMovieTitle }}
            </div>
            <div class="d-flex">
                <strong>Voto:&nbsp;</strong>

                <div v-for="i in 5" :key="i">
                    <i v-if="i <= starGaverate" class="fa-solid fa-star text-warning"></i>
                    <i v-else class="fa-regular fa-star"></i>
                </div>
            </div>
            <div><strong>Overview:</strong>{{ " " + movie.overview }}</div>




        </div>
    </div>


</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    data() {
        return {
            baseUrl: "https://image.tmdb.org/t/p/",
            posterSize: "w300",
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
        originalMovieTitle() {
            if (this.movie.original_title) {
                return this.movie.original_title;
            } return this.movie.original_name;
        },
        starGaverate() {
            return Math.round(this.movie.vote_average / 2);
        },
        //voglio che imageControl possa verificare se movie.poster_path è nul e se è nulo allora metto una immagine di default
        imageControl() {
            if (this.movie.poster_path) {
                return this.baseUrl + this.posterSize + this.movie.poster_path;
            } else {
                return "../img/imgError.png";
            }
        },


    },
    methods: {

    },
}
</script>

<style lang="scss" scoped>
.card-container {}

.card {
    background-color: black;
    border-radius: 0;
    display: inline-block;
    padding: 0.5rem;
    max-height: 465px;

}

.card-absolute {
    overflow: auto;
    text-align: start;
    padding: 0.5rem;
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    opacity: 0;
    transition: opacity 0.5s ease-in-out;


    &:hover {
        opacity: 1;
    }

}
</style>