<template>
    <div class='row'>
        <my-quote v-for="(quote,index) in quotes" :key="index" @click.native="deleteQuote(index)">
            {{ quote }}
        </my-quote>
    </div>
</template>

<script>
    import Quote from "./Quote.vue";
    export default {
        props : ['quotes'],
        components : {
            'my-quote' : Quote
        },
        methods: {
            deleteQuote(index){
                this.$emit('quoteDeleted',index);
            }
        }
    }
</script>

<style scoped>

</style>