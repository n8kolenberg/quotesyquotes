<template>
    <div class="row">
<!-- adding click.native modifer because app-quote doesn't get added to the DOM, the html template does. The .native modifier tells Vue that it needs to delete the HTML template-->
        <app-quote v-for="(quote, index) in quotes" @click.native="deleteQuote(index)">{{quote}}</app-quote>
    </div>
</template>

<script>
import Quote from "./Quote.vue"

export default {
    props: ['quotes'],
    components: {
        'app-quote': Quote
    },
    methods: {
        deleteQuote(index) {
            this.$emit("deleteQuote", index)
        }
    }
}
</script>

<style>

</style>
