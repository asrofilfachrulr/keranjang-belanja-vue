<template>
    <div class="mt-5">
        <div class="row custom-row-title">
            <h2>Keranjang Belanja</h2>
        </div>
        <div class="row custom-table-title">
            <span class="col-3">Name</span>
            <span class="col-3">Quantity</span>
            <span class="col-2">Price</span>
        </div>
        <div v-for="(item, index) in cartItems" :key="index">
            <cart-row-component
                :item="item"
                :index="index"
                @delete="deleteHandle"
                @deleteOne="deleteOneHandle"
            >
            </cart-row-component>
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
            data-bs-toggle="modal"
            data-bs-target="#checkoutModal"
        ></button-component>
        <checkout-modal-component
            :cartItems="cartItems"
            :total="total"
        ></checkout-modal-component>
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
        },
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
        deleteHandle(index) {
            console.log("emit delete to cart");
            this.$emit("delete", index);
        },
        deleteOneHandle(index) {
            console.log("emit delete one to cart");
            this.$emit("deleteOne", index);
        },
        checkoutHandleClick() {
            // alert(`You have to pay Rp. ${this.total}`)
            console.log("checkout pressed, modal should been displayed");
        },
    },
};
</script>

<style></style>
