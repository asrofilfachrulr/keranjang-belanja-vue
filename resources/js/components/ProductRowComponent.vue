<template>
    <div>
        <span class="col" id="prod-name">{{ name }}</span>
        <span class="col" id="prod-desc">{{ desc }}</span>
        <span class="col" id="prod-stock">{{ stock }}</span>
        <span class="col" id="prod-price">{{ price }}</span>
        <button-component></button-component>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            name: "Product Name",
            desc: "This is product description",
            stock: 99,
            price: "Rp. 6900"
        }
    }
}
</script>

<style>

</style>