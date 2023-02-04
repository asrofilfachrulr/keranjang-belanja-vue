<template>
    <div
        class="d-flex flex-column justify-content-center align-items-between"
        id="resetmodalcontent"
    >
        <div id="qrcode-container"></div>
        <p id="order-id">
            code - <span>{{ bodyData.id }}</span>
        </p>
        <p>Show this QRcode to Cashier to proceed your checkout</p>
    </div>
</template>

<script>
export default {
    props: {
        bodyData: {
            type: Object,
            required: true,
        },
    },
};
</script>

<style>
#resetmodalcontent {
    padding-block-start: 1rem;
    gap: 3rem;
    text-align: center;
    font-weight: 400;
}

#order-id > span {
    font-weight: 300;
    letter-spacing: 0.3px;
}

#qrcode-container {
    margin: 0 auto;
}
</style>
