<template>
    <div>
        <select class="form-select" v-model="state.artistaSelezionato" @change="onChangeArtist()">
            <option value="0" selected>Seleziona il tuo Artista</option>
            <option v-for="(artista, i) in fetchArtist" :key="i" :value="artista">{{ artista}}</option>
        </select>       
    </div>
</template>

<script>
import { state } from '../store.js'

export default {
    name: 'SelectArtist',
    methods: {
        onChangeArtist() {
            console.log(state.artistaSelezionato)
        }
    },
    computed: {
        fetchArtist() {
            const artistsList = [];

            state.discList.forEach((disco) => {
                if (!artistsList.includes(disco.author)) {
                    artistsList.push(disco.author)
                }
            })
            return artistsList
        },
        state() {
            return state;
        }
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