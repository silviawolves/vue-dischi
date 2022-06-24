<template>
    <div class="header">
        <img src="/img/logo-small.svg" alt="spotify logo">
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
    padding: .5rem 1.5rem;

    img {
        height: 40px;
        border-radius: 50%;
        background-color: #000;        
    }
}
</style>