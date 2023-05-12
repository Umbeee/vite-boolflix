<script>

import { store } from '../store';
import SingleCard from './SingleCard.vue';

export default {
    name: "MovieCards",
    data() {
        return { store };
    },
    components: { SingleCard }
}

</script>


<template>
    <div class="d-flex flex-wrap container py-3 cards-contaiener">
        <SingleCard v-for="(elem, index) in store.arrayFilm" :key="index" :info="elem" />
    </div>
    <div class="d-flex flex-wrap container py-3 cards-contaiener">
        <SingleCard v-for="(elem, index) in store.arrayTV" :key="index" :info="elem" />
    </div>
</template>

<style lang="scss" scoped>
.cards-contaiener {
    gap: 6.6666%;
}
</style>