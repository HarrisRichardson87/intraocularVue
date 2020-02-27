<template>
  <div id="app">
  
      <Nav v-bind="$props" v-on:filterToFather="test($event)"/>


  </div>
</template>
<script>

import Nav from "./components/Nav.vue";
import axios from 'axios'

export default {
  name:"App",
  components:{
    'Nav': Nav,
   }, 
   props: [
    
    ],
    data: function(){
     return{
         search:'',
         info: null
     }
    }, 
  methods:{
  test(dataFilters){
      this.search = dataFilters;
    },
  },
  mounted () {
    axios.get('http://localhost:5000/leagues/by/Premier/2018/')
      .then((response) => {
        this.info = response
        this.props = {response}
        })
  },
    
}

</script>
<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
