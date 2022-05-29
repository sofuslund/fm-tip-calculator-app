<script>
export default {
    props: ["amount", "label", "sublabel"]
};
</script>

<template>
    <div class="price-tag">
        <div class="price-text">
            <h1 class="price-label">{{label}}</h1>
            <p class="price-sublabel">{{sublabel}}</p>
        </div>
        <p class="price-amount">${{amount}}</p>
    </div>
</template>

<style scoped>
.price-tag {
    width: 100%;
    margin: 1.5em 0;
    overflow: hidden;
}
.price-text {
    float: left;
    margin: auto 0;
}
.price-amount {
    font-size: 2rem;
    color: var(--strong-cyan);
    margin: auto 0;
    display: block;
    height: 100%;
    float: right;
}
.price-label {
    font-weight: 700;
    font-size: .8rem;
    color: var(--white);
}
.price-sublabel {
    font-size: .8rem;
    color: var(--grayish-cyan);
}
</style>
