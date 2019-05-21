<template>
    <div class="new-quote">
        <h4 class="new-quote__title">Quote</h4>
        <div class="new-quote__wrap">
            <textarea class="new-quote__textarea" v-model="quoteText"></textarea>
        </div>
        <button class="new-quote__add btn btn-primary" @click="addQuote">
            Add Quote
        </button>
    </div>
</template>

<script>
    import { eventBus } from '../main.js';

    export default {
        name: "addNewQuote",
        data: function() {
            return {
                quoteText: ''
            }
        },
        methods: {
            addQuote() {
                eventBus.$emit('addQuote', this.quoteText);
                this.quoteText = '';
            }
        }
    }
</script>

<style scoped>
    .new-quote {
        margin: 0 auto 20px;
        width: 600px;
        text-align: center;
    }

    .new-quote__title {
        text-align: left;
    }

    .new-quote__wrap {
        margin-bottom: 20px;
    }

    .new-quote__textarea {
        width: 100%;
        height: 100px;
    }
</style>