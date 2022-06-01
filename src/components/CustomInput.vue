<script>
export default {
    data() {
        return {
            inputStyle: {
                background: `url("${this.icon}") no-repeat .5em center/auto .7em var(--very-light-grayish-cyan)`,
            },
        };
    },
    computed: {
        value: {
            get() {
                return this.modelValue;
            },
            set(val) {
                this.$emit("update:modelValue", val);
            }
        }
    },
    mounted() {
    },
    props: { modelValue: [Number, String], label: String, icon: String, cantBeZero: Boolean, placeholder: String},
    emits: ["update:modelValue"]
};
</script>

<template>
    <div>
        <div>
            <label class="label" for="input">{{ label }}</label>
            <label
                class="label cant-be-zero-label"
                v-show="cantBeZero && value == 0"
                for="input"
            >
                Can't be zero
            </label>
        </div>
        <input
            class="input"
            :placeholder="placeholder"
            :style="inputStyle" 
            type="number"
            min="0"
            v-model="value"
            id="input"
        />
    </div>
</template>

<style scoped>
.label {
    float: left;
    margin: 0.5em 0;
    color: var(--grayish-cyan);
}
.cant-be-zero-label {
    float: right;
    color: red !important;
}
.input {
    vertical-align: middle;
    border: none;
    outline: none;
    text-align: right;
    border-radius: 5px;
    font-size: 1.5rem;
    color: var(--very-dark-cyan);
    width: 100%;
    padding: .2em 0.5em;
}
.input:focus {
    outline: 2px solid var(--strong-cyan);
}
</style>
