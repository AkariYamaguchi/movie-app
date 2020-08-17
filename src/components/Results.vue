<template>
  <div class="container">
      <h1>{{movie_list}}</h1>
  </div>
</template>

<script>
import axios from 'axios';
const apiurl = 'http://www.omdbapi.com/?s=mummy&apikey=ae4b01b0&page=1&type=movie&Content-Type=application/json'

export default {
    data(){
      return{
        movie_list: ''
      }
    },
    mounted(){
      var self = this;
      axios.get(apiurl).then(function(res) {
      self.movie_list = res.data.Search;
      console.log(self.movie_list);
    })
    }
}
</script>

<style scoped>

</style>