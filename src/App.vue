<template>
<div id="app">
    <h1>GIFY</h1>
    <search v-on:SearchRequested="handleSearch"></search>
    <p v-if="isLoading">Loading</p>
    <preview :gifs="gifs"></preview>
</div>
</template>

<script>
import Search from "./components/Search.vue"
import Preview from "./components/Preview.vue"
export default {
    
    name: "app",
    components: {
        Search,
        Preview
    },
    data() {
        return {
            YOUR_API_KEY: 'your key',
            isLoading: true,
            gifs: []
        }
    },
    methods: {
        doQuery(url) {
            fetch(url)
                .then(res => {
                    return res.json()
                })
                .then(res => {
                    this.gifs = res.data
                    this.isLoading = false
                });
        },
        handleSearch(query) {
            this.gifs = []
            this.isLoading = true
            const url = `http://api.giphy.com/v1/gifs/search?q=${query}&api_key=${this.YOUR_API_KEY}`;
            this.doQuery(url)
        }
    },
    created() {
        const url =
            `http://api.giphy.com/v1/gifs/trending?api_key=${this.YOUR_API_KEY}`
        this.doQuery(url)
    }
}
</script>

<style>
#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 30px;
}

#app h1 {
    margin-top: 0%;
    font-size: 100px;
    color: aquamarine;
}

#app p {
    font-size: 100px;
}
</style>
