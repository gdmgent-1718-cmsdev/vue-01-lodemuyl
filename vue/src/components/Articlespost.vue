<template>
  <div class="articlespost">
    <h1>Deze template voegt artikkels toe</h1>
    <h2>{{ msg }}</h2>
    
  </div>
</template>

<script>
export default {
  name: 'articlespost',
  data () {
    return {
      msg: 'via de post methode voegt men artikkels toe aan de backend van d8 '
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #35495E;
}
</style>
