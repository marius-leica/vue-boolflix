<template>
    <div class="bg-dark">
        <div class="container">
            <div class="d-flex justify-content-between align-items-center">
                <div><img src="/img/logo.png" width="150px" alt=""></div>
                <div class="input-group w-50 py-3">
                    <input type="text" class="form-control" placeholder="Cerca Film" v-model="searchText"
                        @keyup.enter="$emit('searchChanged', searchText)" />
                    <button class="btn btn-outline-primary" type="button" @click="$emit('searchChanged', searchText)">
                        Cerca
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            searchText: "",
        };
    },
    methods: {},
};
</script>

<style>
</style>
