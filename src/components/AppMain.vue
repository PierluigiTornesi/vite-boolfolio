<script>
import axios from 'axios';

export default{
  data(){
    return{
        baseUrl: 'http://127.0.0.1:8000',
        projects: [],
    }
  },created(){
    axios.get(`${this.baseUrl}/api/projects`)
        .then((resp) =>{
            //controllo resp per vedere cosa ricevo
            console.log(resp);
            //salvo i dati 
            this.projects = resp.data.results;
            //verifico che siano arrivati i dati
            console.log(this.projects);
        })
  }
}

</script>

<template>
  <h2>Main component</h2>
</template>

<style lang="scss" scoped>

</style>
