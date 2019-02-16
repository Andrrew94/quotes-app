<template>
    <div class="container">
      <Header :quoteCount="quotes.length" :maxQuotes="maxQuotes"/>
      <NewQuote @createQuote="addQuote" />
      <QuotesGrid :quotes="quotes" @deleteQuote="deleteQuote"/>
      <div class="row">
        <div class="col-sm-12 text-center">
          <div class="alert alert-info">Info: Click a quote to delete it!</div>
        </div>
      </div>
    </div>
</template>

<script>
import QuotesGrid from './components/QuotesGrid.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/Header.vue';

    export default {
      data: function() {
        return {
          quotes: ['Some random quote for testing'],
          maxQuotes: 10
        }
      },
      methods: {
        addQuote(quote) {
          if (this.quotes.length >= this.maxQuotes) {
            return alert('The maximum number of quotes has been reached, please delete some quotes')
          };
          this.quotes.push(quote);
        },
        deleteQuote(index) {
          this.quotes.splice(index, 1);
        }
      },
      components: {
        QuotesGrid,
        NewQuote,
        Header
      }
    }
</script>

<style>

</style>
