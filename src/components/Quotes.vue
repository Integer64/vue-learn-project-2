<template>
    <div class="quotes">
        <div class="row">
            <appQuote v-for="(quote, index) in quotesArray" :key="index" :id="index">
                {{ quote.text }}
            </appQuote>
        </div>
    </div>
</template>

<script>
    import Quote from './Quote.vue';
    import { eventBus } from '../main.js';

    export default {
        name: "quotes",
        data: function () {
            return {
                quotesArray: [
                    {
                        text: 'This is Test quote! This is Test quote!'
                    },
                    {
                        text: 'This is Test quote 2!'
                    }
                ]
            }
        },
        components: {
            appQuote: Quote,
        },
        created() {
            eventBus.$on('removeQuote', (quoteId)=> {
                this.quotesArray.splice(quoteId, 1);
            });

            eventBus.$on('addQuote', (quoteText)=> {
                console.log(this.quotesArray.length);
                if(this.quotesArray.length < 10) {
                    const quote = {
                        text: quoteText
                    };
                    this.quotesArray.push(quote);
                } else {
                    alert('Too many Quotes! Delete some before adding new ones!');
                }
            });

            eventBus.$emit('quotesArrayLength', this.quotesArray.length);
        },
        watch: {
            quotesArray: function () {
                eventBus.$emit('quotesArrayLength', this.quotesArray.length);
            }
        }
    }
</script>

<style scoped>
</style>