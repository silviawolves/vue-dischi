<template>
    <div class="header">
        <img src="/img/logo-small.svg" alt="spotify logo">
        <div class="d-flex gap-3">
            <SelectArtist></SelectArtist>
            <SelectGenre></SelectGenre>
        </div>
    </div>
</template>

<script>
import SelectGenre from "./SelectGenre.vue";
import SelectArtist from "./SelectArtist.vue";

export default {
    name: "TheHeader",
    components: { SelectGenre, SelectArtist }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.header {
    background-color: $primary;
    flex-shrink: 0;
    padding: .5rem 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
        height: 40px;
        border-radius: 50%;
        background-color: #000;        
    }
}
</style>