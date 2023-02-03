<template>
    <div>
        <div class="row">
            <span class="col-3">{{ item.name }}</span>
            <span class="col-3">{{ item.qty }}</span>
            <span class="col-2">{{ item.price }}</span>
            <button-component
                :btnType="btnTypeDelOne"
                @click="delOneHandleClick"
                class="mr-3"
            >
            </button-component>
            <button-component
                :btnType="btnTypeDel"
                @click="delHandleClick"
            ></button-component>
        </div>
    </div>
</template>

<script>
export default {
    props: ["item", "index"],
    data: function () {
        return {
            btnTypeDel: {
                text: "Delete",
                type: "danger",
            },
            btnTypeDelOne: {
                text: 'Reduce',
                type: "outline-danger",
            },
        };
    },
    methods: {
        delHandleClick() {
            console.log("emit delete to ListCart");
            this.$emit("delete", this.index);
        },
        delOneHandleClick() {
            console.log("emit delete one to ListCart")
            this.$emit("deleteOne", this.index)
        }
    },
};
</script>

<style>
.row-no-border {
    border: none;
}
</style>
