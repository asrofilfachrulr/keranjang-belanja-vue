<template>
    <div>
        <span class="col-3" id="prod-name">{{ product.name }}</span>
        <span class="col-5" id="prod-desc">{{ product.desc }}</span>
        <span class="col-1" id="prod-stock">{{ product.stock }}</span>
        <span class="col-1" id="prod-price">{{ product.price }}</span>
        <button-component
            @click="handleClick"
            class="col-2"
            :btnType="btnType"
        ></button-component>
    </div>
</template>

<script>
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
            btnType: {
                text: "Add to cart",
                type: "primary",
            },
        };
    },
    methods: {
        handleClick() {
            this.$emit('add', this.index)
        },
    },
};
</script>

<style></style>
