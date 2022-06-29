<template>
    <div>
        <div id="moviesList">
            <ul class="list-group">
                <li class="list-group-item" v-for="movie in moviesList" :key="movie.id">
                    <MovieCard :movie="movie"></MovieCard>

                </li>
            </ul>
            <!-- Stampare una MovieCard per ogni film -->
        </div>

        <div id="seriesList">
            <!-- Stampare una MovieCard per ogni film -->
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
        searchMovies() {
            axios
                .get("https://api.themoviedb.org/3/search/movie", {
                    params: {
                        api_key: "66da9c9715a8aa6ea7123977e1274068",
                        query: this.userInput,
                        language: "it-IT",
                    },
                })
                .then((response) => {
                    console.log(response.data.results);
                    this.moviesList = response.data.results;
                });
            // .catch(() => {
            //   this.moviesList = [];
            // });
        },
        onSearchChange() {
            this.searchText = this.userInput;
            this.searchMovies();
        },
    },
    watch: {
        userInput() {
            this.onSearchChange();
        },
    },
    components: { MovieCard }
};
</script>

<style>
</style>
