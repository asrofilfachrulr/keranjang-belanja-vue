<template>
    <div>
        <button-component :btnType="btnTypes.Cancel" :data-bs-dismiss="'modal'">
        </button-component>
        <button-component
            :btnType="btnTypes.Print"
            :data-bs-dismiss="'modal'"
            @click="handlePrintClick"
        ></button-component>
    </div>
</template>

<script>
export default {
    props: {
        btnTypes: {
            type: Object,
            required: true,
        },
    },
    methods: {
        handlePrintClick() {
            alert(
                `Your order has been registered by ID ${
                    Math.floor(Math.random() * 1000) + "-" + Date.now()
                }, Please wait a waiter/ess comes to you`
            );
        },
    },
};
</script>

<style></style>
