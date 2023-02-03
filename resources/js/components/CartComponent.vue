<template>
    <div class="container-fluid">
        <list-product-component
            :products="products"
            @add="addCartItem"
        ></list-product-component>
        <list-cart-component
            :cartItems="cartItems"
            :total="cartTotal"
            @delete="deleteCartItem"
            @deleteOne="deleteOneCartItem"
        ></list-cart-component>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            products: Vue.observable([
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
            ]),
            cartItems: {},
            cartTotal: 0,
        };
    },
    methods: {
        addCartItem(index) {
            let product = this.products[index];
            if (!this.cartItems[index])
                Vue.set(this.cartItems, index, {
                    name: product.name,
                    qty: 1,
                    price: product.price,
                });
            else
                Vue.set(this.cartItems, index, {
                    ...this.cartItems[index],
                    qty: this.cartItems[index].qty + 1,
                });

            Vue.set(this.products, index, {
                ...this.products[index],
                stock: this.products[index].stock - 1,
            })
        },
        deleteCartItem(index) {
            console.log("catch delete event");
            Vue.set(this.products, index, {
                ...this.products[index],
                stock: this.cartItems[index].qty + this.products[index].stock
            })
            Vue.delete(this.cartItems, index);
            console.log(this.cartItems);
        },
        deleteOneCartItem(index) {
            console.log("catch delete one event");

            Vue.set(this.products, index, {
                ...this.products[index],
                stock: this.products[index].stock + 1
            })

            if(this.cartItems[index].qty == 1){
                this.deleteCartItem(index)
                return
            }

            Vue.set(this.cartItems, index, {
                ...this.cartItems[index],
                qty: this.cartItems[index].qty - 1
            })
            console.log(this.cartItems);
        },
        calculateTotal() {
            this.cartTotal = 0;
            
            if (Object.keys(this.cartItems).length == 0) return 0;

            console.log(JSON.stringify(this.cartItems));
            for (let index in this.cartItems) {
                this.cartTotal +=
                    this.cartItems[index].price * this.cartItems[index].qty;
            }
        },
    },
    watch: {
        cartItems: {
            handler() {
                console.log("calculating new total..");
                this.calculateTotal();
            },
            deep: true,
        },
    },
};
</script>

<style></style>
