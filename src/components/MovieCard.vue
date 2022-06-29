<template>
    <div>
        <div>{{ movie.title }}</div>
        <div>{{ movie.original_title }}</div>
        <div>{{ movie.original_language }}</div>
        <div>{{ movie.vote_average }}</div>
    </div>
</template>

<script>
export default {
    props: {
        movie: Object,

    },
}
</script>

<style>
</style>