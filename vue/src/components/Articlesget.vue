<template>
  <div class="articlesget">
    <h2>Deze template haalt alle artikkels op</h2>
    <form v-on:submit.prevent="getartk">
      <div class="row">
        <div class="col s12">
          welke node wil je ophalen ?
          <div class="input-field inline">
            <input id="numb" v-model.number="node"></label>
          </div>
        </div>
      </div>
    </form>
    
    <div class="container">
    <div class="collection">
        <div class="collection-item blue lighten-2">
          <h4>{{ post.title }}</h4>
        </div>
        <div class="collection-item #64b5f6 blue lighten-2">
          {{ post.body }}
        </div>    
      </div>
    </div>
      
      
     <ul v-if="errors && errors.length">
    <li v-for="error of errors">
      {{error.message[0].value}}
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
      post: {
        title: '',
        body: ''
      },   
      node: 19,   
      errors: []
    }
  },
methods: {
  getartk () {
    this.$update;
    console.log(this.$data.node);
  }

},
update(){ console.log("updated") },
created() {
  console.log('in created');
    axios.get(`http://localhost:8080/node/`+ this.$data.node +`?_format=hal_json`)
      .then(response => {
          
      // JSON responses are automatically parsed.
      this.post.title = response.data.title[0].value;
      this.post.body = response.data.body[0].value
      
    })
    .catch(e => {
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
