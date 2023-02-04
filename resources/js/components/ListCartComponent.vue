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
        <div class="row row-no-border mt-3">
            <button-component
                :btnType="btnTypeCheckout"
                @click="checkoutHandleClick"
                data-bs-toggle="modal"
                :data-bs-target="'#' + checkoutModalId"
                :disabled="Object.keys(this.cartItems) <= 0"
            ></button-component>
            <button-component
                class="ml-3"
                :btnType="btnTypeClearAll"
                :disabled="Object.keys(this.cartItems) <= 0"
                @click="clearAllHandleClick"
            ></button-component>
        </div>
        <centered-modal
            :modalId="checkoutModalId"
            :bodyData="{
                cartItems,
                total,
            }"
            :componentBody="checkoutComponentBody"
            :componentFooter="checkoutComponentFooter"
            :modalTitle="'Checkout'"
            :btnTypes="checkoutBtnTypesModal"
            @actionClick="checkoutActionClickHandle"
        ></centered-modal>
        <centered-modal
            :modalId="resetModalId"
            :bodyData="{
                id: orderId,
            }"
            :componentBody="resetComponentBody"
            :componentFooter="resetComponentFooter"
            :modalTitle="'Checkout Done'"
            :btnTypes="resetBtnTypesModal"
        ></centered-modal>
    </div>
</template>

<script>
import CheckoutModalContent from "./CheckoutModalContent.vue";
import CheckoutModalFooterVue from "./CheckoutModalFooter.vue";
import ResetModalContent from "./ResetModalContent.vue";
import ResetModalFooter from "./ResetModalFooter.vue";

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
            btnTypeClearAll: {
                text: "Clear All",
                type: "danger",
            },
            checkoutComponentBody: CheckoutModalContent,
            checkoutComponentFooter: CheckoutModalFooterVue,
            resetComponentBody: ResetModalContent,
            resetComponentFooter: ResetModalFooter,
            checkoutModalId: "checkoutModal",
            resetModalId: "resetModal",
            checkoutBtnTypesModal: {
                Cancel: {
                    text: "Cancel",
                    type: "secondary",
                },
                Print: {
                    text: "Print",
                    type: "primary",
                },
            },
            resetBtnTypesModal: {
                OK: {
                    text: "Okay",
                    type: "primary",
                },
            },
            orderId: "",
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
        clearAllHandleClick() {
            console.log("emit clear all to cart");
            this.$emit("clearAll");
        },
        checkoutActionClickHandle(id) {
            this.orderId = id;
            // toggle reset modal
            $("#" + this.resetModalId).modal("toggle");
            console.log(`generating qrcode with id ${id}`);

            var qr = qrcode(4, "H");
            qr.addData(id);
            qr.make();
            var svg = qr.createSvgTag(4, 4);

            document.getElementById("qrcode-container").innerHTML = svg;

            document.getElementById(
                "qrcode-container"
            ).children[0].style.transform = "scale(1.25)";
            // clear all cart
            this.clearAllHandleClick();
        },
    },
};
</script>

<style></style>
