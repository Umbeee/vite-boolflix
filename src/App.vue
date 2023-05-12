<script>
import { store } from './store';
import HeaderApp from './components/HeaderApp.vue';
import MovieCards from './components/MovieCards.vue';

export default {

    name: "App",
    data() {
        return { store }
    },
    components: { HeaderApp, MovieCards },
    created() {
        this.searchFunct();
    },
    methods: {
        searchFunct() {
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${store.apiKey}&query=${store.valueFiltro}`)
                .then((res) => {
                    store.arrayFilm = res.data.results
                })
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${store.apiKey}&query=${store.valueFiltro}`)
                .then((res) => {
                    store.arrayTV = res.data.results
                })
        }
    }

}
</script>

<template>
    <HeaderApp @apiCall="searchFunct()" />
    <MovieCards />
</template>

<style lang="scss" scoped></style>
