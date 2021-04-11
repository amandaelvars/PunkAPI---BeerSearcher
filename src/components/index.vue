<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
      <div class="search-input">
        <input v-on:keypress.enter="searchbeer()" v-model="search" type="text" placeholder="Search Beer">
        <a href="#" class="searchbar-clear"></a>
        <button class="searchclear" @click="searchbeer()">Search</button>
        <button class="searchclear" @click="clearsearch()">Clear</button>
      </div>
      <div class="nobeer">
        <div v-if = "nobeer">
          <p class="nobeer">No beer with this name...</p>
        </div>
      </div>
    <!-- for each beer in the beers collection, render a beer component !-->
      <div class="divgrid">
        <div class="column" v-for="(beer,index) in beers" :key="index">
          <Beer :beerData="beer"></Beer>
        </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
import Beer from './Beer.vue'
export default {
  components:{
    Beer
  },
  name: 'Index',
  props: {
    msg: String
  },
  data(){
    return{
      beers:[],
      search:'',
      nobeer:false
    }
  },

  methods: {
    searchbeer(){
      if (this.search != ''){
        axios.get('https://api.punkapi.com/v2/beers?beer_name=' + this.search)
          .then((res) => {
          this.beers = res.data;
          this.nobeer = false;
            if (res.data.length == 0) {
              this.nobeer = true;
            }
          })
      /*}else{
        axios.get('https://api.punkapi.com/v2/beers')
        .then((res) => {
          this.beers = res.data
          this.search = ''
          this.nobeer = false
        })*/
      }
    },
    clearsearch(){
      axios.get('https://api.punkapi.com/v2/beers')
          this.beers = []
          this.search = ''
          this.nobeer = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input{
  width: 300px;
}
.nobeer{
  font-weight:bold;
  color: black;
}
.searchclear{
  margin-right:2px;
}
.divgrid{
  justify-content: center;
  align-content: center;
  margin-top: 20px;
  display: grid;
  grid-template-columns: 300px 300px 300px 300px;
}
.column{
  border-radius: 10px;
  background-color:rgb(248, 248, 248);
  margin-left:10px;
  margin-right:10px;
  margin-top: 10px;
  margin-bottom: 10px;
}
</style>
