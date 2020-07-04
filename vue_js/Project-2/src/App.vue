<template>
	<div id="container">
		<app-progress-bar :quoteCount='quotes.length' :maxQuotes="maxQuotes"></app-progress-bar>
		<app-new-quote @quoteAdded="newQuote"></app-new-quote>
		<app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
		<div class="col-sm-12 text-center">
			<div class="alert alert-info">
				Click on the Quote to delete
			</div>
		</div>
	</div>
</template>

<script>
	import QuoteGrid from './components/QuoteGrid.vue';
	import NewQuote from './components/NewQuote.vue';
	import ProgressBar from './components/ProgressBar.vue';

	export default {
		data: function() {
			return {
				quotes : [
					'Just a Quote to see something'
				],
				maxQuotes : 10
			}
		},
		methods :{
			newQuote(quote){
				if(this.quotes.length >= this.maxQuotes){
					return alert('Please delete Quotes first');
				}
				this.quotes.push(quote);
			},
			deleteQuote(index){
				this.quotes.splice(index,1);
			}
		},
		components: { 
			'app-quote-grid' : QuoteGrid,
			'app-new-quote' : NewQuote,
			'app-progress-bar': ProgressBar
		}
	}
</script>

<style>
</style>
