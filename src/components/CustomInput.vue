<script>
export default {
    data() {
        return {
            value: 0,
            inputStyle: {
                background: `url("${this.icon}") no-repeat .5em center/auto .7em var(--very-light-grayish-cyan)`,
            },
        };
    },
    mounted() {
        console.log(this.$slots.default);
        // value = parseInt(this.$refs.placeholder.innerText);
    },
    props: { label: String, icon: String, cantBeZero: Boolean },
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
