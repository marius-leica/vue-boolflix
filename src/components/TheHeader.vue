<template>
    <div>
        <form class="d-flex mb-5">
            <div class="input-group">
                <input type="text" class="form-control" placeholder="Cerca Film" v-model="searchText" />
                <button class="btn btn-outline-primary" type="button" @click="$emit('searchChanged', searchText)">
                    Cerca
                </button>

            </div>
        </form>
    </div>
</template>

<script>
export default
    {
        data() {
            return {
                searchText: "",
            };
        },
    }


</script>

<style>
</style>
