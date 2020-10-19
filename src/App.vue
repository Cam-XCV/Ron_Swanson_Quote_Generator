<template>
  <div id="main-container">
    <div id="title-container">
    <h1> The Wise Words of Ron Swanson</h1>
    <img src="./assets/ron.png" alt=":)" id="ron-png">
    </div>
      <quote-selection :quotes="quotes" />
      <quote-display :quote="selectedQuote" />
  </div>
</template>

<script>
import { eventBus } from './main.js'
import QuoteSelection from "./components/QuoteSelection"
import QuoteDisplay from "./components/QuoteDisplay"


export default {
  data(){
    return {
      quotes: null,
      selectedQuote: null
    }
  },

  components: {
    'quote-selection': QuoteSelection,
    'quote-display': QuoteDisplay
  },
  
  mounted(){
    fetch("http://ron-swanson-quotes.herokuapp.com/v2/quotes/110")
    .then(res => res.json())
    .then(data => this.quotes = data) 

    eventBus.$on('selected-quote', (quote) => {
      this.selectedQuote = quote
    })

  }

  }
</script>

<style>

#main-container {
  margin: auto;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  display: flex;
  flex-flow: column;
  align-items: center;
}

h1 {
  color: rgb(82, 59, 59);
}
#title-container {
  display: flex;
  flex-flow: column;
  align-items: center;
}

#ron-png {
  width: 200px;
  padding: 20px;
}

</style>
