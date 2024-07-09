<script lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
import axios from 'axios'
export default{
  data(){
    return{
      list:[],
      list2:[],
      busqueda:""
    }
  },
  methods:{
    vermas : async function(valor){
      console.log(valor);
      let result2 = await axios.post("http://127.0.0.1:8000/api/getFilteredReviews",{
        idComment : parseInt(this.valor)
      });
    console.log(result2.data);
      this.list2 = result2.data.reviews

    },
    Buscar : async function(){
      let result = await axios.post("http://127.0.0.1:8000/api/getMoviesByName",{
        name : this.busqueda
      });
    console.log(result.data.reviews);
      this.list = result.data.reviews
    }
  },
  async mounted(){
    this.Buscar();
  }
}


</script>

<template>
  <div class="movies">
    <h1>Movies</h1>
    <input type="text" placeholder="Intensamente.." style="width: 80%; height: 30px; border-radius: 25px;" name="busqueda" v-model="busqueda">
    <input type="button" value="Buscar" style="width: 20%; height: 30px; border-radius: 25px;" @click="Buscar()">
      <div v-for="item in list" :key="item.id">
        <h2>{{ item.name }}</h2><br>
        <img v-bind:src="item.imgurl" width="200">
        {{item.synopsis}}
        <button type="button" value="Ver Más" @click="vermas(item.id)" style="width: 20%; height: 30px; border-radius: 25px;">Ver más</button>
        <hr>
      </div>
  </div>
  <div class="ModalMovie">
  <h1></h1>
  </div>
  
</template>


<style>
.movies{
  overflow:scroll; height:100%;
}
</style>