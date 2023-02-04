<template>
    <div
        class="modal fade"
        :id="modalId"
        tabindex="-1"
        aria-labelledby="checkoutModalLabel"
        aria-hidden="true"
    >
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header justify-content-center">
                    <h1 class="modal-title fs-5" id="exampleModalLabel">
                        {{ modalTitle }}
                    </h1>
                </div>
                <div class="modal-body">
                    <component
                        :is="componentProp"
                        :bodyData="bodyData"
                    ></component>
                </div>
                <div class="modal-footer">
                    <button-component
                        :btnType="btnTypeCancel"
                        :data-bs-dismiss="'modal'"
                    >
                    </button-component>
                    <button-component :btnType="btnTypeDone"
                        >Done</button-component
                    >
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        modalId: {
            type: String,
        },
        bodyData: {
            type: Object,
            default: () => {},
        },
        modalTitle: {
            type: String,
            default: "",
        },
        componentProp: {
            type: Object,
            required: true,
        },
    },
    data: function () {
        return {
            btnTypeDone: {
                text: "Done",
                type: "success",
            },
            btnTypeCancel: {
                text: "Cancel",
                type: "secondary",
            },
        };
    },
};
</script>

<style></style>
