<template>
  <nav class="navbar navbar-white bg-white justify-content-between shadow-sm">
          <a to='/' class="navbar-brand">
            <img src='../assets/hamsa.png' width="30" height="30" alt="logo" >
           intr()cular
         </a>
        <form class="form-inline" v-on:submit="submit">
          <input class="form-control mr-sm-2" v-model="search"  @keyup="prueba" list="browsers" name="browsers" type="search" v-on:change='keyup' aria-label="Search"/>
          <!-- {this.renderSuggestions()} -->
          <a to='/search'><button class="btn btn-outline-success my-2 my-sm-0" type="submit" >Search</button></a>
        </form>
      </nav>



</template>

<script>
export default {
  name:"Nav",
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
      alert(this.search)


    } 
     
  },
  
}
</script>
