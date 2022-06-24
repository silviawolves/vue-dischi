<template>
    <div class="main">
        <div class="container py-5">

            <!--barra di selezione generi musicali-->
            <div class="d-flex justify-content-end pb-4">
                <select class="form-select">
                    <option selected>Seleziona il genere dal menù</option>
                    <option v-for="(generi, i) in discList" :key="i" :value="i">{{ generi.genre }}</option>
                </select>
            </div>

            <!--card singoli album-->
            <div class="row row-cols-5 gx-5 gy-3 mx-5">
                <div class="col" v-for="(dischi, i) in discList" :key="i">
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
        }
    },
    methods: {
        fetchDiscList() {
            axios.get(this.apiUrl).then((risultato) => {
                this.discList = risultato.data.response
            })
        }
    },
    mounted() {
        this.fetchDiscList()
    }
}
</script>


<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.main {
    background-color: $secondary;
    flex-grow: 1;
}

select {
    width: 25%;
    font-size: .8rem;
    color: white;
    background-color: $primary;
    margin-right: 4.5rem;
}
</style>