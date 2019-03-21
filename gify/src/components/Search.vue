<template>
<div class="search">
    <input type="text" v-model="query" @keypress.enter="handleSearch">
    <button @click="handleSearch">Search</button>
</div>
</template>

<script>
export default {
    data() {
        return {
            query: ""
        };
    },
    methods: {
        handleSearch() {
            this.$emit("SearchRequested", this.query);
        }
    }
};
</script>

<style>
.search input {
    padding: 10px 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 50%;
    height: 20%;
    font-size: 2em;
    margin-top: 0%;
}

.search button {
    padding: 10px 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: aquamarine;
    font-size: 2em;
}
</style>
