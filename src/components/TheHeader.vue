<template>
    <div class="header">
        <img src="/img/logo-small.svg" alt="spotify logo">
        <SelectBar></SelectBar>
    </div>
</template>

<script>
import SelectBar from "./SelectBar.vue";

export default {
    name: "TheHeader",
    components: { SelectBar }
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