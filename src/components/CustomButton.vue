<script>
export default {
    data() {
        return {

        }
    }
}
</script>

<template>
    <button class="custom-btn">
        <slot></slot>
    </button>
</template>

<style scoped>
.custom-btn {
    color: var(--very-dark-cyan);
    background-color: var(--strong-cyan);
    font-size: 1rem;
    width: 100%;
    height: 2.5em;
    border: none;
    border-radius: .3em;
}
</style>