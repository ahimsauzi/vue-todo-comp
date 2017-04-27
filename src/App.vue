<template>
    <div class="container">
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-header :quoteCount="quotes.length" :maxQuote="maxQuote"></app-header>
        <div class="row">
            <div class="col-sm-12t text-center">
                <div class="alert alert-info">Info: Click on a quote to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './component/QuoteGrid.vue';
    import NewQuote from './component/NewQuote.vue';
    import Header from './component/Header.vue';

    export default {
            data: function () {
                return {
                    quotes: [
                        'Just a placeholder to see someting'
                    ],
                    maxQuote: 10
                }
            },
            methods: {
                newQuote (quote) {
                    if(this.quotes.length >= this.maxQuote) {
                        return alert('Please delete Quote first!');
                    }
                    this.quotes.push(quote);
                },
                deleteQuote(index) {
                    this.quotes.splice(index, 1);
                }
            },
            components: {
                appQuoteGrid: QuoteGrid,
                appNewQuote: NewQuote,
                appHeader: Header
            }
    }
</script>

<style>
</style>
