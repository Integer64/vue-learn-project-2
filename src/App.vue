<template>
    <div class="container">
        <div class="row">
            <appHeader :class="col-xs-12"></appHeader>
            <appAddNewQuote :class="col-xs-12"></appAddNewQuote>
            <appQuotes :class="'col-xs-12'"></appQuotes>
            <div class="info col-xs-12">
                <span class="text-info">Info: Click on a Quote to delete it</span>
            </div>
        </div>

    </div>
</template>

<script>
    import Quotes from './components/Quotes.vue';
    import AddNewQuote from './components/AddNewQuote.vue';
    import Header from './components/Header.vue';

    export default {
        components: {
            appQuotes: Quotes,
            appAddNewQuote: AddNewQuote,
            appHeader: Header
        }
    }
</script>

<style scoped>
    .info {
        background-color: lightblue;
        padding: 20px;
        margin: 20px auto;
        text-align: center
    }
</style>
