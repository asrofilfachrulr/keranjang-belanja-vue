<template>
    <div>
        <div class="row">
            <span class="col-3">{{ item.name }}</span>
            <span class="col-3">{{ item.qty }}</span>
            <span class="col-3">{{ item.price }}</span>
            <button-component
                class="col-3"
                :btnType="btnTypeDel"
                @click="delHandleClick"
            ></button-component>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        item: {
            type: Object,
            default: () => {},
        }
    },
    data: function () {
        return {
            btnTypeDel: {
                text: "Delete",
                type: "danger",
            },
        };
    },
    methods: {
        delHandleClick() {
            alert('Delete clicked');
        },
    }
};
</script>

<style>
.row-no-border {
    border: none;
}
</style>
