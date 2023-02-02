<template>
    <div>
        <div class="row">
            <h2 class="col"> {{ title }} </h2>
        </div>
        <div class="row">
            <span class="col">Name</span>
            <span class="col">Description</span>
            <span class="col">Stock</span>
            <span class="col">Price</span>            
            <div class="w-100"></div>
            <product-row-component></product-row-component>
        </div>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            title: "Semua Produk" 
        }
    }
}
</script>

<style>

</style>