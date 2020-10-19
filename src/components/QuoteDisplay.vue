<template>
  <div id="quote-container" v-if="quote">
    <p>{{quote}}</p>
  </div>
</template>

<script>
export default {
    name: 'quote-display',
    props: ['quote']
}
</script>

<style>

#quote-container {
    margin: 20px;
    padding:20px;
    text-align: center;
    width: 650px;
    background-color: rgb(97, 84, 84);
    color:white;
}
</style>