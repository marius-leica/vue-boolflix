<template>
    <div>
        <div id="moviesList">
            <ul>
                <li class="border" v-for="movie in moviesList" :key="movie.id">
                    <div>{{ movie.title }}</div>
                    <div>{{ movie.original_title }}</div>
                    <div>{{ movie.original_language }}</div>
                    <div>{{ movie.vote_average }}</div>


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


export default {
    props: {
        userInput: String
    },
    data() {
        return {
            moviesList: [],
            seriesList: [],
        };
    },

    methods: {
        searchMovies() {
            axios.get("https://api.themoviedb.org/3/search/movie", {
                params: {
                    api_key: "66da9c9715a8aa6ea7123977e1274068",
                    query: this.userInput,
                    language: "it-IT",
                },

            })
                .then((response) => {
                    console.log(response.data.results);
                    this.moviesList = response.data.results;
                }).catch(() => {
                    this.moviesList = [];
                });
        }
    },
    mounted() {
        this.searchMovies();
    },

};
</script>

<style>
</style>
