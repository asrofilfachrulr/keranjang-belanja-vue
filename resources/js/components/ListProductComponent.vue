<template>
    <div>
        <div class="row custom-row-title">
            <h2 class="col"> {{ title }} </h2>
        </div>
        <div class="row custom-table-title">
            <span class="col-3">Name</span>
            <span class="col-5">Description</span>
            <span class="col-1">Stock</span>
            <span class="col-1">Price</span>            
        </div>
        <product-row-component class="row" v-for="(product, index) in products" :key="index" :product="product"></product-row-component>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            title: "Semua Produk",
            products: [
            {
                    name: "Indomie Goreng Rendang",
                    desc: "Masakan Instan Terenak di Dunia",
                    stock: 10,
                    price: 3900,
                },
                {
                    name: "Mie Gelas Rendang",
                    desc: "Masakan Instan Khusus Anak Kostan",
                    stock: 3,
                    price: 1500,
                },
                {
                    name: "Bakmi Mewah",
                    desc: "Kalau Anak Kosan Jangan Macem-Macem Deh",
                    stock: 80,
                    price: 10000,
                },
            ] 
        }
    }
}
</script>

<style>

</style>