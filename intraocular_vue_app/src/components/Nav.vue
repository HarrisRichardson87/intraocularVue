<template>
  <nav id="Nav" class="navbar navbar-white bg-white justify-content-between shadow-sm">
          <a to='/' class="navbar-brand">
            <img src='../assets/hamsa.png' width="30" height="30" alt="logo" >
           intr()cular
         </a>
        <form class="form-inline" v-on:submit="submit">
          <input  list="browsers" name="browsers" autocomplete="off" class="form-control mr-sm-2" v-model="search" @keyup="suggester"  type="search" v-on:change='keyup' aria-label="Search"/>
         
           <datalist id="browsers">
    v-for="item in items" :key="item.message"
  
      <option v-for="(item, index) in suggestions" :key="index"> {{item}}Premier League </option>
    
    </datalist>
          <a to='/search'><button class="btn btn-outline-success my-2 my-sm-0" type="submit" >Search</button></a>


        </form>
      </nav>


</template>

<script>
import axios from 'axios'
export default {
  name:"Nav",
 data: function(){
     return{
        suggestions:[],
        text:'',
        dataBox:null
     }},
  props: {
    msg: String,
  },
  methods: {
    toggleNavbar() {
      this.navbarOpen = !this.navbarOpen;
    },
    submit(e){
      e.preventDefault()
      this.$emit('filterToFather', this.search)
    },   suggester(e){
      e.preventDefault()
      this.text = e.target.value
      const value = e.target.value
      let suggestions = [];
       if(value.length > 0){
      let regex = new RegExp(`^${value}`, 'i')
      let copy = this.dataBox
      suggestions = copy.sort().filter(v => regex.test(v))
      // alert(suggestions)
    this.suggestions = suggestions
    }
    }
  },
  mounted () {
    axios.get('http://localhost:5000/leagues/by/Premier/2018/')
      .then((response) => {
       
        return response
        }).then((json) =>{
         
          this.dataBox =json.data[0].seasons[0].players.map(player => player.name)

        })
  },

 
  
  
}
</script>
