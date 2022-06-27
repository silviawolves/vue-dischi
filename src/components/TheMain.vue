<template>
    <div class="main">
        <div class="container py-5">

            <div class="row row-cols-5 gx-5 gy-3 mx-5">
                <template v-if="!state.artistaSelezionato">
                    <div class="col" v-for="(dischi, i) in filteredGenre" :key="i">
                        <CardDisco :disc-img="dischi.poster" :disc-title="dischi.title" :disc-author="dischi.author" :disc-year="dischi.year"></CardDisco>
                    </div>
                </template>

                <template v-if="!state.genereSelezionato">
                    <div class="col" v-for="(dischi, i) in filteredArtist" :key="i">
                        <CardDisco :disc-img="dischi.poster" :disc-title="dischi.title" :disc-author="dischi.author" :disc-year="dischi.year"></CardDisco>
                    </div>
                </template>
            </div>
            
        </div>
    </div>
</template>

<script>
import CardDisco from './CardDisco.vue'
import axios from 'axios'
import { state } from '../store.js'

export default {
    name: "TheMain",
    components: { CardDisco },
    data() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
        }
    },
    methods: {
        fetchDiscList() {
            axios.get(this.apiUrl).then((risultato) => {
                state.discList = risultato.data.response;
            })
            .catch(() => {
                alert("L'operazione non è andata a buon fine.")
            })
        },
    },
    mounted() {
        this.fetchDiscList()
    },
    computed: {
        state() {
            return state
        },
        filteredGenre() {
            if (!state.genereSelezionato) {
                return state.discList
            }

            return state.discList.filter((element) => {
                return element.genre === state.genereSelezionato
            })
        },
        filteredArtist() {
            if (!state.artistaSelezionato) {
                return state.discList
            }

            return state.discList.filter((element) => {
                return element.author === state.artistaSelezionato
            })
        },
    },
}
</script>


<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.main {
    background-color: $secondary;
    flex-grow: 1;
    overflow: auto;

    select {
        width: 25%;
        font-size: .8rem;
        color: white;
        background-color: $primary;
        margin-right: 4.5rem;
    }
}
</style>