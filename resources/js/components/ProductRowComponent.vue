<template>
    <div>
        <span
            class="col-3"
            id="prod-name"
            @click="productModalClick"
            data-bs-toggle="modal"
            :data-bs-target="'#' + modalId"
            style="cursor: pointer"
            >{{ product.name }}</span
        >
        <span class="col-5" id="prod-desc">{{ product.desc }}</span>
        <span class="col-1" id="prod-stock">{{ product.stock }}</span>
        <span class="col-1" id="prod-price">{{ product.price }}</span>
        <button-component
            v-bind:disabled="product.stock <= 0"
            @click="handleClick"
            :btnType="btnType"
        ></button-component>
        <centered-modal
            :bodyData="{
                src: product.src,
                desc: product.longDesc,
            }"
            :componentProp="componentProp"
            :modalTitle="product.name"
            :modalId="modalId"
        ></centered-modal>
    </div>
</template>

<script>
import ProductModalContent from "./ProductModalContent.vue";

export default {
    props: {
        product: {
            type: Object,
            default: () => [],
        },
        index: {
            type: Number,
            default: () => -1,
        },
    },
    data: function () {
        return {
            bodyData: {},
            btnType: {
                text: "Add to cart",
                type: "primary",
            },
            componentProp: ProductModalContent,
            modalId: this.product.name.replace(/\s/g, "") + "Modal",
        };
    },
    methods: {
        handleClick() {
            this.$emit("add", this.index);
        },
        productModalClick() {
            console.log(
                "product has been clicked, modal should been displayed"
            );
        },
    },
};
</script>

<style>
#prod-name {
    text-decoration: underline;
}
</style>
