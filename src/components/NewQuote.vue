<template>
    <div class="row">
        <form action="">
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
                <label>Quote</label>
                <!-- 2 way binding textarea with quote through v-model to ensure that the typed in quote can get emitted through the createNew() method -->
                <textarea class="form-control" name="" id="" cols="30" rows="3" v-model="quote"></textarea>
            </div>
             <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
                <button class="btn btn-primary" type="submit" @click.prevent="createNew" >Add Quote</button>
            </div>     
        </form>
        
        
    </div>
</template>

<script>

export default {
    data() {
        return {
            quote: ''
        }
    },
    methods: {
        createNew() {
            this.$emit('quoteAdded', this.quote);
            this.quote = "";
        }
    }
}
</script>

<style>
    .row {
        padding-top: 30px;
        padding-bottom: 30px;
    }
</style>
