<template>
  <div id="search-container">
      <button v-on:click="handleClick">Randomise Wisdom</button>
      <p>or</p>
      <input type="text" v-model="search" placeholder="Looking for something specific?" v-on:keyup="searchForQuote">
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: "quote-selection",

    data(){
        return {
            search: null,
            selectedQuote: null
        }
    },

    props: ['quotes'],

    methods: {
        handleClick() {
            let randIndex = Math.floor(Math.random() * 111)
            this.selectedQuote = this.quotes[randIndex]

            eventBus.$emit('selected-quote', this.selectedQuote)
        },

        
        //this needs fixed
        searchForQuote(){
            let foundQuotes = this.quotes.filter((quote) => {
                return this.quotes.includes(this.search)})                
            this.selectedQuote = foundQuotes
            

            eventBus.$emit('selected-quote', this.selectedQuote) 
        }
    }
}
</script>

<style>
#search-container {
    display: flex;
    width: 500px;
    justify-content: space-between;
    padding: 10px;
}


button {
    background-color: rgb(97, 84, 84);
    font-size: 15px;
    color: white;
    border: none;
    width:45%;
}

button:focus {
    outline:0;
}

button:hover {
    cursor: pointer;
}

input {
    width: 45%;
    font-size: 15px;
    text-align: center;
    border: 1px, solid, rgb(80, 67, 67)
}
</style>