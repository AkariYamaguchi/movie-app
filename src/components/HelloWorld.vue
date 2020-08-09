<template>
  <div>
    <div v-if="users">
      <h1 class='user' v-for="(user, index) in users" :key="index">
      {{user.company.name}}
    </h1>
    </div>
    <h1>wating user info....</h1>
  </div>
</template>

<script>
import axios from 'axios';

const users = 'https://jsonplaceholder.typicode.com/users';

export default {
  name: 'HelloWorld',
  data () {
    return {
      users:''
    }
  },
  mounted(){
    var self = this;
    axios.get(users)
     .then(function (res){
       self.users = res.data;
       console.log(self.users);
     })
     .catch((error) => {
       console.log(
         "エラーです。"
       );
    });
   },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<!-- helloworld.vueのCSS -->
<style scoped>
.title {
  color: red;
}
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
  color: #42b983;
}
</style>
