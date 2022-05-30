<script>
import CustomInput from "./components/CustomInput.vue";
import CustomButton from "./components/CustomButton.vue";
import PriceTag from "./components/PriceTag.vue";
import NumberRadio from "./components/NumberRadio.vue";

export default {
    data() {
        return {
            personTipAmount: 0,
            total: 0,
        };
    },
    components: {
        CustomInput,
        CustomButton,
        NumberRadio,
        PriceTag,
    },
};
</script>

<template>
    <div class="root-flexbox">
        <img class="root-flex-item logo" src="./assets/img/logo.svg" alt="logo" />
        <div class="root-flex-item flexbox">
            <div class="flex-item">
                <section>
                    <CustomInput
                        label="Bill"
                        icon="/src/assets/img/icon-dollar.svg"
                    ></CustomInput>
                </section>
                <section>
                    <NumberRadio
                        label="Select Tip %"
                        :values="[5, 10, 15, 25, 50]"
                        suffix="%"
                    ></NumberRadio>
                </section>
                <section>
                    <CustomInput
                        label="Number of People"
                        icon="/src/assets/img/icon-person.svg"
                        cantBeZero
                    ></CustomInput>
                </section>
            </div>
            <div class="flex-item result-container">
                <section class="price-result">
                    <div class="price-tag-container">
                        <PriceTag
                            class="price-tag"
                            label="Tip Amount"
                            sublabel="/ person"
                            :amount="personTipAmount"
                        ></PriceTag>
                        <PriceTag
                            label="Total"
                            sublabel="/ person"
                            :amount="total"
                        ></PriceTag>
                    </div>
                    <CustomButton class="btn">RESET</CustomButton>
                </section>
            </div>
            <div class="attribution">
                Challenge by
                <a
                    href="https://www.frontendmentor.io?ref=challenge"
                    target="_blank"
                >
                    Frontend Mentor
                </a>
                . Coded by
                <a href="#">Sofus</a>
                .
            </div>
        </div>
    </div>
</template>

<style>
@import "./assets/styles/base.css";
@import url("https://fonts.googleapis.com/css2?family=Space+Mono:wght@700&display=swap");
:root {
    --strong-cyan: hsl(172, 67%, 45%);
    --very-dark-cyan: hsl(183, 100%, 15%);
    --dark-grayish-cyan: hsl(186, 14%, 43%);
    --grayish-cyan: hsl(184, 14%, 56%);
    --light-grayish-cyan: hsl(185, 41%, 84%);
    --very-light-grayish-cyan: hsl(189, 41%, 97%);
    --white: hsl(0, 0%, 100%);
}
* {
    font-family: "Space Mono", monospace;
    font-weight: 700;
}
/* Disable arrows from number inputs */
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}

#app {
    height: 100vh;
}
body {
    background-color: var(--light-grayish-cyan);
}
html {
    font-size: .85rem;
}
@media screen and (min-width: 375px) {
    html {
        font-size: clamp(.85rem, 1.4vh + .2rem, 1rem);
    }
}
</style>
<style scoped>
.root-flexbox {
    display: flex;
    flex-direction: column;
    height: 100%;
}
.root-flex-item.logo {
    flex: 0 1 auto;
}
.root-flex-item.flexbox {
    flex: 1 1 auto;
}
.attribution {
    position: fixed;
    bottom: 5px;
    left: 50%;
    transform: translate(-50%, 0);
}
.logo {
    transform: scale(0.8);
    margin: 0 auto;
    padding: 2rem 0;
    display: block;
}
.flexbox {
    background-color: var(--white);
    border-radius: 1rem 1rem 0 0;
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    width: 100%;
    min-height: fit-content;
}
.flex-item {
    padding: 0 2em;
}
section {
    margin: 1.6em 0;
}
.result-container {
    padding: 0 1.7em;
    overflow: hidden;
}
.price-result {
    background-color: var(--very-dark-cyan);
    border-radius: .8em;
    padding: 1.5em;
    margin-top: 0;
    margin-bottom: 1.5em;
}
.price-tag:first-child {
    margin-top: .5em;
}
.btn {
    /* margin-top: 1.2em; */
    margin-bottom: 0.1em;
}

@media screen and (min-width: 562px) {
    .root-flexbox {
        justify-content: center;
        align-items: center;
    }
    .flexbox {
        border-radius: 1rem;
        flex-direction: row;
        flex-wrap: nowrap;
        justify-content: space-evenly;
        align-items: stretch;

        flex-grow: 0 !important;
        max-width: 55em;
        margin-bottom: 5em;
    }
    .flex-item {
        flex-grow: 1;
        width: 50%;
        padding: 2em;
    }
    .result-container {
        padding-left: .5em;
    }
    section {
        margin: 1em 0;
    }
    .price-result {
        display: flex;
        justify-content: space-between;
        flex-direction: column;
        margin: 0 0;
        height: 100%;
    }
}
</style>
