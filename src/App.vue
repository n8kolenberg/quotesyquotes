<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <!--@quoteAdded is an event emitted by createNew method in NewQuote.vue-->
        <!--addNewQuote is the method here that will push the quote to the quotes array-->
        <new-quote @quoteAdded="addNewQuote"></new-quote>
        <!-- Binding quotes to quotes array so we can use it as a prop in QuoteGrid-->
        <!-- with @deleteQuote, we're listening for that event coming from the quoteGrid -->
        <my-quote-grid :quotes="quotes" @deleteQuote="deleteQuoteNow"></my-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a Quote to delete it
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue"
import NewQuote from "./components/NewQuote.vue"
import Header from "./components/Header.vue"


    export default {
        data() {
            return {
                maxQuotes: 10,
                quotes: ["Just to see a quote", "To see another quote"],
            }
        },
        methods: {
            addNewQuote(quote) {
                if(this.quotes.length >= this.maxQuotes) {
                    alert("Whoops - too many quotes for us to handle! Could you remove some?")
                } else {
                    this.quotes.push(quote);
                }
                
            },
            deleteQuoteNow(index) {
                this.quotes.splice(index,1);
            }
        },
        components: {
            'my-quote-grid': QuoteGrid,
            'new-quote': NewQuote,
            'app-header': Header
        },
        
    }
</script>

<style>
</style>
