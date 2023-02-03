<template>
    <div
        class="modal fade"
        id="checkoutModal"
        tabindex="-1"
        aria-labelledby="checkoutModalLabel"
        aria-hidden="true"
    >
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header justify-content-center">
                    <h1 class="modal-title fs-5" id="exampleModalLabel">
                        Checkout
                    </h1>
                </div>
                <div class="modal-body">
                    <div
                        class="d-flex justify-content-start align-items-center mb-3"
                        v-for="(item, index) in cartItems"
                        :key="index"
                    >
                        <span id="checkout-item-name">{{ item.name }}</span>
                        <span id="checkout-item-qty">
                            {{ item.qty }}
                        </span>
                        <span class="ms-auto" id="checkout-item-price">
                            Rp. {{ item.price }}
                        </span>
                    </div>
                    <div
                        class="d-flex justify-content-end align-items-end"
                        id="flex-total"
                    >
                        <span id="checkout-total">Total</span>
                        <span id="checkout-total-price">Rp. {{ total }}</span>
                    </div>
                </div>
                <div class="modal-footer">
                    <button-component
                        :btnType="btnTypeCancel"
                        :data-bs-dismiss="'modal'"
                    >
                    </button-component>
                    <button-component :btnType="btnTypeDone"
                        >Done</button-component
                    >
                </div>
            </div>
        </div>
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
            default: 0,
        },
    },
    data: function () {
        return {
            btnTypeDone: {
                text: "Done",
                type: "success",
            },
            btnTypeCancel: {
                text: "Cancel",
                type: "secondary",
            },
        };
    },
};
</script>

<style>
#checkout-item-name {
    font-weight: 500;
    min-width: 12rem;
    max-width: 12rem;
}
#checkout-item-qty {
    min-width: 2rem;
    max-width: 2rem;
    margin-inline-start: 1rem;
}
#checkout-item-price {
    min-width: 6rem;
    max-width: 6rem;
    text-align: end;
}
#checkout-item-price,
#checkout-total-price {
    font-weight: 600;
}
#flex-total {
    gap: 1.5rem;
}
#checkout-total-price {
    border-top: 1px dashed #7c7d7e;
    padding-top: 1rem;
    /* border-style: ; */
}
</style>
