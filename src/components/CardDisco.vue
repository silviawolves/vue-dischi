<template>
    <div class="my-card">
        <img :src="discImg" :alt="`Album ${discTitle}`">
        <div class="title">{{ discTitle }}</div>
        <div class="author">{{ discAuthor }}</div>
        <div class="year"> {{ discYear }}</div>
    </div>
</template>

<script>
export default {
    name: 'CardDisco',
    props: {
        discImg: String,
        discAuthor: String,
        discTitle: String,
        discYear: String,
    },
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.my-card {
    background-color: $primary;
    width: 100%;
    height: 100%;
    padding: 1rem;
    text-align: center;

    img {
        aspect-ratio: 1/1;
        width: 100%;
        display: block;
    }

    .title {
        padding: 1rem 0;
        text-transform: uppercase;
        font-size: 1.5rem;
        color: white;
        font-weight: bold;
        line-height: 100%;
    }

    .author, .year {
        color: gray;
    }
}
</style>