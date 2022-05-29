<script>
import CustomButton from "./CustomButton.vue";
import CustomInput from "./CustomInput.vue";
export default {
    data() {
        return {
            selected: NaN,
        }
    },
    methods: {
        btnClick(idx) {
            this.selected = idx;
        }
    },
    props: ["suffix", "values", "label"], 
    components: {
        CustomButton, 
        CustomInput
    }
}
</script>

<template>
<div>
    <p class="label">{{label}}</p>
    <div class="flexbox">
        <CustomButton class="btn flex-item" @click="btnClick(idx)" :class="{selected: selected == idx}" v-for="(value, idx) in values">
            {{value}}{{suffix}}
        </CustomButton>
        <CustomInput class="flex-item">Custom</CustomInput>
    </div>
</div>
</template>

<style scoped>
    .label {
        margin: .5em 0;
        color: var(--grayish-cyan);
    }
    .flexbox {
        display: flex;
        flex-wrap: wrap;
        margin: 0 -.4rem;
    }
    .flex-item {
        width: calc(50% - 2 * .4rem);
        margin: .4rem;
        /* padding: .3em 3em; */
    }
    .btn {
        background-color: var(--very-dark-cyan);
        color: var(--white);
    }
    .selected {
        background-color: var(--strong-cyan);
        color: var(--very-dark-cyan);
    }
</style>