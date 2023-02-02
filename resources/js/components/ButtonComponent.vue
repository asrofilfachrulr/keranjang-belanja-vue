<template>
    <button class="btn" :class="btnToApply" type="button">{{ btnType.text }}</button>
</template>

<script>
export default {
    props: {
        btnType: {
            type: Object,
            default: () => {
                return {
                    text: 'Button',
                    type: 'primary'
            }
            },
        }
    },
    computed: {
        btnToApply(){
            return "btn-"+this.btnType.type
        }
    }
}
</script>

<style>
.btn {
    min-width: min-content;
    max-width: fit-content;
    padding: 0.5rem 0.75rem;
}
</style>