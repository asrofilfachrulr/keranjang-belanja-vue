<template>
    <div>
        <div class="row custom-row-title">
            <h2 class="col">{{ title }}</h2>
        </div>
        <div class="row custom-table-title">
            <span class="col-3">Name</span>
            <span class="col-5">Description</span>
            <span class="col-1">Stock</span>
            <span class="col-1">Price</span>
        </div>
        <div v-for="(product, index) in products" :key="index">
            <product-row-component
                class="row"
                :product="product"
                :index="index"
                @add="emitAdd"
            ></product-row-component>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        products: {
            type: Array,
            default: () => [],
        },
    },
    data: function () {
        return {
            title: "Semua Produk",
        };
    },
    methods: {
        emitAdd(data) {
            this.$emit("add", data);
        },
    },
};
</script>

<style></style>
