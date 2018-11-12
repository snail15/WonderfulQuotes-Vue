<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
       <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import Newquote from './components/NewQuotes.vue';
    import Header from './components/Header.vue';
    export default {
        data: function(){
            return{
                quotes: ['Just a Quote to see something'],
                maxQuotes: 10
            }
           
        },

        components:{
            appQuoteGrid:QuoteGrid,
            'app-new-quote': Newquote,
            appHeader: Header
        },

        methods: {
            newQuote: function(quote){
                if(this.quotes.length >= this.maxQuotes){
                    return alert("Max Capacitt Reached! Delete Quotes");
                }
                this.quotes.push(quote);
            },
            deleteQuote: function(index){
                this.quotes.splice(index,1);
            }
        }

    }
</script>

<style>
</style>
