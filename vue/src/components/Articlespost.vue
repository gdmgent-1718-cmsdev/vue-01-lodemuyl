<template>
  <div class="articlespost">
    <h2>Deze template voegt artikkels toe</h2>
    <form class="container" v-on:submit.prevent="createpost">
    
      <div class="row">
        <div class="input-field col s12">
          <input  id="first_name2" type="text" class="validate" v-model="title">
          <label class="active" for="first_name2">Titel</label>
        </div>
      </div>
      <div class="row">
        <div class="col s12">
          <div class="row">
            <div class="input-field col s12">
              <textarea id="icon_prefix2" class="materialize-textarea" v-model="message"></textarea>
              <label for="icon_prefix2">Bericht</label></label>
            </div>
          </div>
        </div>
      </div>
      <button class="btn waves-effect waves-light" type="submit" name="action" >Post
      <i class="material-icons right">send</i>
      </button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'articlespost',
  data () {
    var config = {
           headers: {
            'Accept': 'application/hal+json',
            'Content-Type': 'application/hal+json',
            'X-CSRF-Token': 'iKnpqGkq9jNSmZu-MxkAMxu_zYTJbN6bys1eL4uiBoA',
            'Authorization': 'basic Y21zZGV2LXVzZXI6Y21zZGV2LXBhc3M='
          }
    }  
    return {
      msg: 'via de post methode voegt men artikkels toe aan de backend van d8 ',
      title: "derde",
      message: "derde",
      config: config
    }
  },
  methods: {
    createpost: () => {
      axios.post('http://localhost:8080/node', 
      { 
          "_links": {
            "type": {
              "href": "http://localhost:8080/rest/type/node/article"
            }
          },
          "title": {
            "value": this.title
          },
          "type": {
            "target_id": "article"
          } 
      }, this.config)
          .then(function(response) {
              console.log('opgeslaan')
          })
          .catch(function(error) {
              console.log(error);
          });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1, h2 {
  font-weight: normal!important;
}

ul {
  list-style-type: none!important;
  padding: 0!important;
}

li {
  display: inline-block!important;
  margin: 0 10px!important;
}

a {
  color: #35495E;
}
</style>
