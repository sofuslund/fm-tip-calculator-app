<script>
import { nextTick } from "vue";
import CustomButton from "./CustomButton.vue";
import CustomInput from "./CustomInput.vue";
export default {
    data() {
        return {
            selected: NaN,
            inputVal: "",
        };
    },
    methods: {
        async btnClick(idx, val) {
            this.inputVal = "";
            // When the input value gets altered it is now the selected tip percentage. 
            // To avoid this we first alter the input value and then wait for the dom 
            // to update in "next tick" and then change the selected index
            await nextTick();
            this.selected = idx;
            this.$emit("updateVal", val);
        },
    },
    watch: {
        inputVal(v) {
            this.selected = NaN;
            this.$emit("updateVal", parseFloat(this.inputVal) || 0);
        }, 
        resetTrigger() {
            this.selected = NaN;
            this.inputVal = "";
        }
    },
    props: ["resetTrigger", "suffix", "values", "label", "modelValue"],
    emits: ["updateVal"],
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
                @click="btnClick(idx, value)"
                :class="{ selected: selected == idx }"
                :key="idx"
            >
                {{ value }}{{ suffix }}
            </CustomButton>
            <CustomInput v-model="inputVal" placeholder="Custom" class="flex-item input"></CustomInput>
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
