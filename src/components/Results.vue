<template>
    <h1>これはテスト</h1>
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
      self.movies_list = res.data.Search;
      console.log(self.movies_list);
    })
    }
}
</script>

<style scoped>

</style>