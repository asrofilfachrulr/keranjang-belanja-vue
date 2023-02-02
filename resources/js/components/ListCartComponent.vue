<template>
    <div class="mt-4">
        <div class="row custom-row-title">
            <h2>Keranjang Belanja</h2>
        </div>
        <div class="row custom-table-title">
            <span class="col-3">Name</span>
            <span class="col-3">Quantity</span>
            <span class="col-3">Price</span>
        </div>
        <div v-for="(item, index) in cartItems" :key="index">
            <cart-row-component :item="item"></cart-row-component>
        </div>
        <div class="row custom-total-row">
            <span class="col-3">Total:</span>
            <span class="col-3"></span>
            <span class="col-3">Rp. {{ total }}</span>
            <span class="col-3"></span>
        </div>
        <button-component
            class="row row-no-border mt-3"
            :btnType="btnTypeCheckout"
            @click="checkoutHandleClick"
        ></button-component>
    </div>
</template>

<script>
export default {
    props: {
        cartItems: {
            type: Object,
            default: () => {},
        },
        total: {
            type: Number,
            default: () => 0,
        }
    },
    data: function () {
        return {
            btnTypeCheckout: {
                text: "Checkout",
                type: "success",
            },
        };
    },
    methods: {
        checkoutHandleClick() {
            alert("Checkout clicked");
        },
    },
};
</script>

<style></style>
