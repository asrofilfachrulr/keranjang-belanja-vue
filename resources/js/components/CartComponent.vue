<template>
    <div class="container-fluid">
        <list-product-component
            :products="products"
            @add="addCartItem"
        ></list-product-component>
        <list-cart-component
            :cartItems="cartItems"
            :total="cartTotal"
        ></list-cart-component>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
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
            ],
            cartItems: {},
            cartTotal: 0,
        };
    },
    methods: {
        addCartItem(index) {
            let product = this.products[index];
            if (!this.cartItems[index])
                this.cartItems[index] = {
                    name: product.name,
                    qty: 1,
                    price: product.price,
                };
            else this.cartItems[index].qty += 1;
            console.log(this.cartItems)
            this.calculateTotal();
        },
        calculateTotal() {
            if (this.cartItems == {}) return 0;

            for(let index in this.cartItems){
                this.cartTotal += this.cartItems[index].price * this.cartItems[index].qty;
            };
        },
    },
};
</script>

<style></style>
