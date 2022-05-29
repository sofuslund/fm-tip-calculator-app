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
    <img class="logo" src="./assets/img/logo.svg" alt="logo" />
    <div class="flex-container">
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
body {
    background-color: var(--light-grayish-cyan);
}
</style>
<style scoped>
.logo {
    transform: scale(0.8);
    margin: 0 auto;
    padding: 1.5rem 0;
    display: block;
}
.flex-container {
    background-color: var(--white);
    border-radius: 1rem 1rem 0 0;
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    /* position: relative; */
    /* bottom: 0; */
}
.flex-item {
    padding: 0 1.5em;
}
section {
    margin: 1.6em 0;
}
.result-container {
    padding: 0 1em;
}
.price-result {
    background-color: var(--very-dark-cyan);
    border-radius: 10px;
    padding: 1em;
    margin-bottom: 1.5em;
}
.btn {
    /* margin-top: 1.2em; */
    margin-bottom: 0.1em;
}
</style>
