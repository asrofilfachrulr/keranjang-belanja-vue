<template>
    <div>
        <div class="row d-flex flex-nowrap">
            <span class="col-3">{{ item.name }}</span>
            <span class="col-3">{{ item.qty }}</span>
            <span class="col-2">{{ item.price }}</span>
            <button-component
                :btnType="btnTypeDelOne"
                @click="delOneHandleClick"
                :class="['col-auto', 'mr-2']"
            >
            </button-component>
            <button-component
                :btnType="btnTypeDel"
                :class="['col-auto', 'me-auto']"
                :id="'delete-item'"
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
                text: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash3" viewBox="0 0 16 16"><path d="M6.5 1h3a.5.5 0 0 1 .5.5v1H6v-1a.5.5 0 0 1 .5-.5ZM11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3A1.5 1.5 0 0 0 5 1.5v1H2.506a.58.58 0 0 0-.01 0H1.5a.5.5 0 0 0 0 1h.538l.853 10.66A2 2 0 0 0 4.885 16h6.23a2 2 0 0 0 1.994-1.84l.853-10.66h.538a.5.5 0 0 0 0-1h-.995a.59.59 0 0 0-.01 0H11Zm1.958 1-.846 10.58a1 1 0 0 1-.997.92h-6.23a1 1 0 0 1-.997-.92L3.042 3.5h9.916Zm-7.487 1a.5.5 0 0 1 .528.47l.5 8.5a.5.5 0 0 1-.998.06L5 5.03a.5.5 0 0 1 .47-.53Zm5.058 0a.5.5 0 0 1 .47.53l-.5 8.5a.5.5 0 1 1-.998-.06l.5-8.5a.5.5 0 0 1 .528-.47ZM8 4.5a.5.5 0 0 1 .5.5v8.5a.5.5 0 0 1-1 0V5a.5.5 0 0 1 .5-.5Z"/></svg>',
                type: "danger",
            },
            btnTypeDelOne: {
                text:
                    '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-cart-dash" viewBox="0 0 16 16"><path d="M6.5 7a.5.5 0 0 0 0 1h4a.5.5 0 0 0 0-1h-4z"/><path d="M.5 1a.5.5 0 0 0 0 1h1.11l.401 1.607 1.498 7.985A.5.5 0 0 0 4 12h1a2 2 0 1 0 0 4 2 2 0 0 0 0-4h7a2 2 0 1 0 0 4 2 2 0 0 0 0-4h1a.5.5 0 0 0 .491-.408l1.5-8A.5.5 0 0 0 14.5 3H2.89l-.405-1.621A.5.5 0 0 0 2 1H.5zm3.915 10L3.102 4h10.796l-1.313 7h-8.17zM6 14a1 1 0 1 1-2 0 1 1 0 0 1 2 0zm7 0a1 1 0 1 1-2 0 1 1 0 0 1 2 0z"/></svg>' +
                    "&nbsp;&nbsp;Reduce",
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
            console.log("emit delete one to ListCart");
            this.$emit("deleteOne", this.index);
        },
    },
};
</script>

<style>
.row-no-border {
    border: none;
}
</style>
