<template>
  <div class="articlesget">
    <h1>Deze template haalt alle artikkels op</h1>
    <h2>{{ posts }}</h2>


  <ul v-if="errors && errors.length">
    <li v-for="error of errors">
      {{error.message}}
    </li>
  </ul>

  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'articlesget',
  data () {
    return {
      msg: 'dit zijn alle artikkels uit de backend van d8 ',
      posts: [],
      errors: []
    }
  },
created() {
    axios.get(`http://localhost:4000/node/1?_format=hal_json`)
      .then(response => {
          console.log(response.data);
          console.log('geluuukt');
      // JSON responses are automatically parsed.
      this.posts = response.data
      
    })
    .catch(e => {
      console.log('error');
      this.errors.push(e);
    })
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
