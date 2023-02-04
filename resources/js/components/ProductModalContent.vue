<template>
    <div class="d-flex flex-column justify-content-center">
        <img
            id="modal-product-img"
            v-bind:src="bodyData.src"
            alt="image product"
        />
        <p id="modal-product-desc">{{ bodyData.desc }}</p>
    </div>
</template>

<script>
export default {
    props: {
        bodyData: {
            type: Object,
            default: () => {},
        },
    },
};
</script>

<style>
#modal-product-img {
    max-height: 300px;
    max-width: 100%;
    object-fit: cover;
    border-radius: 10px;
}

#modal-product-desc {
    text-align: center;
}
</style>
