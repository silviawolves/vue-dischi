<template>
    <div>
        <select class="form-select" v-model="state.genereSelezionato" @change="onChange()">
            <option value="0" selected>Seleziona il genere dal menù</option>
            <option v-for="(generi, i) in fetchGenreList" :key="i" :value="generi">{{ generi }}</option>
        </select>
    </div>
</template>

<script>
import { state } from '../store.js'

export default {
    name: 'SelectGenre',
    computed: {
        state() {
            return state;
        },
        fetchGenreList() {
            const genreList = [];
            state.discList.forEach((disco) => {
                if (!genreList.includes(disco.genre)) {
                    genreList.push(disco.genre)
                }
            })
            return genreList
        },
    },
    methods: {
        onChange() {
            console.log(state.genereSelezionato)
        },
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

    select {
        width: 100%;
        font-size: .8rem;
        color: white;
        background-color: $primary;
    }
</style>