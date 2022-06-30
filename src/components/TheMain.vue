<template>

    <div class=" flex-grow-1">
        <div id="moviesList" class="pt-5">
            <div class="row row-cols-3 g-5">
                <div class="col text-center" v-for="movie in moviesList" :key="movie.id">
                    <MovieCard :movie="movie"></MovieCard>
                </div>
            </div>
        </div>

        <div id="seriesList" class="pt-5">
            <div class="row row-cols-3 g-5">
                <div class="col text-center" v-for="movie in seriesList" :key="movie.id">
                    <MovieCard :movie="movie"></MovieCard>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
import axios from "axios";
import MovieCard from "./MovieCard.vue";

export default {
    props: {
        userInput: String,
    },
    data() {
        return {
            moviesList: [],
            seriesList: [],
            searchText: "",
        };
    },
    methods: {
        searchMovies(type) {
            axios
                .get("https://api.themoviedb.org/3/search/" + type, {
                    params: {
                        api_key: "66da9c9715a8aa6ea7123977e1274068",
                        query: this.userInput,
                        language: "it-IT",
                    },
                })
                .then((response) => {
                    if (type === "movie") {
                        this.moviesList = response.data.results;
                        console.log(this.moviesList);
                    } else {
                        this.seriesList = response.data.results;
                        console.log(this.seriesList);
                    }
                });

        },
        onSearchChange() {
            this.searchText = this.userInput;


        },
    },
    watch: {
        userInput() {
            this.onSearchChange();
            this.searchMovies("movie");
            this.searchMovies("tv");
        },
    },
    components: { MovieCard }
};
</script>

<style lang>
</style>
