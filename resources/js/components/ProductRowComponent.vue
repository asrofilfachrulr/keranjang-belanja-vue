<template>
    <div>
        <span class="col-3" id="prod-name">{{ product.name }}</span>
        <span class="col-4" id="prod-desc">{{ product.desc }}</span>
        <span class="col-1" id="prod-stock">{{ product.stock }}</span>
        <span class="col-1" id="prod-price">{{ product.price }}</span>
        <button-component class="col-3"></button-component>
    </div>
</template>

<script>
export default {
    props: {
        product: {
            type: Array,
            default: () => [],
        }
    }
}
</script>

<style>
</style>