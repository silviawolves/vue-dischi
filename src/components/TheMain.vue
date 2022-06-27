<template>
    <div class="main">
        <div class="container py-5">

            <!--barra di selezione generi musicali-->
            <div class="d-flex justify-content-end pb-4">
                <select class="form-select" v-model="valoreSelezionato" @change="onChange()">
                    <option value="0" selected>Seleziona il genere dal menù</option>
                    <option v-for="(generi, i) in fetchGenreList" :key="i" :value="generi">{{ generi }}</option>
                </select>
            </div>

            <!--card singoli album-->
            <div class="row row-cols-5 gx-5 gy-3 mx-5">
                <div class="col" v-for="(dischi, i) in filterGenre" :key="i">
                    <CardDisco :disc-img="dischi.poster" :disc-title="dischi.title" :disc-author="dischi.author" :disc-year="dischi.year"></CardDisco>
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import CardDisco from './CardDisco.vue'
import axios from 'axios'

export default {
    name: "TheMain",
    components: { CardDisco },
    data() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            discList: [],
            valoreSelezionato: 0,
        }
    },
    methods: {
        fetchDiscList() {
            axios.get(this.apiUrl).then((risultato) => {
                this.discList = risultato.data.response;
            })
            .catch(() => {
                alert("L'operazione non è andata a buon fine.")
            })
        },
        onChange() {
            console.log(this.valoreSelezionato)
        },
    },
    mounted() {
        this.fetchDiscList()
    },
    computed: {
        fetchGenreList() {
            const genreList = [];

            this.discList.forEach((disco) => {
                if (!genreList.includes(disco.genre)) {
                    genreList.push(disco.genre)
                }
            })

            return genreList;
        },
        filterGenre() {
            if (!this.valoreSelezionato) {
                return this.discList
            }
            return this.discList.filter((element) => {
                return element.genre === this.valoreSelezionato
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