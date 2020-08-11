<template>
<div>
    <h1>Movie app</h1>
    <div class='container'>
        <Results title='this is movies..'/>
        <li v-for="(movie, index) in movies" :key="index">
        <div class='wrapper_style'>
            <div class="flex">
                <div class='title_style'><h1 class='title'>{{ movie.Title }}</h1></div>
                <div class='img_style'><img class='img' :src="movie.Poster "/></div>
            </div>
        </div>
        </li>
    </div>
</div>
</template>

<script>
import axios from 'axios';
import Results from '../components/Results'
const apiurl = "http://www.omdbapi.com/?s=mummy&apikey=ae4b01b0&page=1&type=movie&Content-Type=application/json";

export default {
    components: {
        Results,
    },
    data(){
        return{
            movies: ''
        }
    },
    mounted(){
        var self = this;
        axios.get(apiurl).then(function(res) {
            self.movies = res.data.Search;
            console.log(self.movies);
        })
    },
    
}
</script>

<style scoped>
.container{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 30px;
}
.wrapper_style{
    border: solid 1px #000;
}
/* .flex{
    display: grid;
    grid-template-columns: 2fr 1fr;
    height: 100%;
} */
</style>