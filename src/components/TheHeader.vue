<template>
    <div>
        <div class="d-flex mb-5">
            <div class="input-group">
                <input type="text" class="form-control" placeholder="Cerca Film" v-model="searchText"
                    @keyup.enter="$emit('searchChanged', searchText)" />
                <button class="btn btn-outline-primary" type="button" @click="$emit('searchChanged', searchText)">
                    Cerca
                </button>
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
