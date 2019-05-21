<template>
    <div class="col-xs-3">
        <div class="quote" @click="removeQuote">
            <slot></slot>
        </div>
    </div>
</template>

<script>
    import { eventBus } from '../main.js';

    export default {
        name: "Quote",
        props: {
            id: {
                type: Number
            }
        },
        methods: {
            removeQuote() {
                eventBus.$emit('removeQuote', this.id);
            }
        }
    }
</script>

<style scoped>
    .quote {
        margin: 0 0 10px 0;
        padding: 10px;
        border: 1px solid;
        border-radius: 5px;
        font-size: 34px;
        line-height: 38px;
        font-family: 'Arizonia', sans-serif;
    }

    .quote:hover {
        cursor: pointer;
        background: rgba(212, 57, 84, 0.5);
    }
</style>