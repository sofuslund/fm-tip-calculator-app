<script>
export default {
    data() {
        return {};
    },
};
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
    font-size: 1.2rem;
    width: 100%;
    padding: .5em 0;
    border: none;
    border-radius: 0.3em;
}
</style>
