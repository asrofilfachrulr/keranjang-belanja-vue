<template>
    <button class="btn" type="button">Add to cart</button>
</template>

<script>
export default {

}
</script>

<style>
.btn {
    min-width: min-content;
    max-width: fit-content;
    padding: 0.5rem 0.75rem;
    border-radius: 5px;
    background-color: #0d6efd;
    color: white;
    border: none;
    transition: all 0.2s ease-in-out;
}

.btn:active {
    filter: opacity(0.75) grayscale(0.1);
}

</style>