<script>
import CustomButton from "./CustomButton.vue";
import CustomInput from "./CustomInput.vue";
export default {
    data() {
        return {
            selected: NaN,
        };
    },
    methods: {
        btnClick(idx) {
            this.selected = idx;
        },
    },
    props: ["suffix", "values", "label"],
    components: {
        CustomButton,
        CustomInput,
    },
};
</script>

<template>
    <div>
        <p class="label">{{ label }}</p>
        <div class="flexbox">
            <CustomButton
                class="btn flex-item"
                v-for="(value, idx) in values"
                @click="btnClick(idx)"
                :class="{ selected: selected == idx }"
                :key="idx"
            >
                {{ value }}{{ suffix }}
            </CustomButton>
            <CustomInput class="flex-item input">Custom</CustomInput>
        </div>
    </div>
</template>

<style scoped>
.label {
    margin: 0.5em 0;
    color: var(--grayish-cyan);
}
.flexbox {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}
.flex-item {
    font-size: 1.2rem;
    flex-grow: 1;
    flex-basis: 45%;
    height: 2.5em;
    padding: 0;
    /* padding: .3em 3em; */
}
.input::deep input {
    font-size: 1.2rem;
    height: 2.5em;
}
.btn {
    background-color: var(--very-dark-cyan);
    color: var(--white);
}
.selected {
    background-color: var(--strong-cyan);
    color: var(--very-dark-cyan);
}
@media screen and (min-width: 425px) {
    .flex-item {
        flex-basis: 30%;
    }
}
</style>
