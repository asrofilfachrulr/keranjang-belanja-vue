<template>
    <div>
        <div class="row">
            <span class="col-3">Name</span>
            <span class="col-3">Quantity</span>
            <span class="col-3">Price</span>
            <button-component
                class="col-3"
                :btnType="btnTypeDel"
            ></button-component>
        </div>
        <div class="row custom-total-row">
            <span class="col-3">Total:</span>
            <span class="col-3"></span>
            <span class="col-3">Rp.3000</span>
            <span class="col-3"></span>
        </div>
        <button-component
            class="mt-3"
            :btnType="btnTypeCheckout"
        ></button-component>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            btnTypeDel: {
                text: "Delete",
                type: "danger",
            },
            btnTypeCheckout: {
                text: "Checkout",
                type: "success",
            },
        };
    },
};
</script>

<style></style>
