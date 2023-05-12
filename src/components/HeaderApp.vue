<script>

import { store } from '../store';

export default {

    name: "HeaderApp",
    data() {
        return {
            store
        }
    }
}

</script>


<template>
    <header>
        <div class="container d-flex justify-content-between p-3 align-items-center">
            <a href=".">
                <h1 class="text-danger">BOOLFLIX</h1>
            </a>

            <div class="d-flex align-items-center justify-content-between">
                <input type="text" v-model="store.valueFiltro" placeholder="Cerca">
                <button type="button" class="btn btn-danger" @click="$emit('apiCall')">Invia</button>
            </div>
        </div>
    </header>
</template>


<style lang="scss" scoped>
header {
    background-color: black;

    .container {
        a {
            text-decoration: none;
        }
    }

    input,
    .btn {
        height: 30px;
        margin: 5px;
    }

    .btn {
        display: flex;
        align-items: center;
    }

}
</style>