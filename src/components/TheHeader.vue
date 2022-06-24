<template>
    <div class="header">
        <img src="/img/logo-small.svg" alt="spotify logo">
        <div class="generi">
            <select class="form-select">
                <option selected>Seleziona il genere dal menù</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
            </select>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TheHeader'
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";
.header {
    background-color: $primary;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: .5rem 1.5rem;

    img {
        height: 40px;
        border-radius: 50%;
        background-color: #000;        
    }

    select {
        font-size: .8rem;
        color: white;
        background-color: $secondary;
    }
}
</style>