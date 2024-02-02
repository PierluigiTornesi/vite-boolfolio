<script>
import axios from 'axios';

export default{
  data(){
    return{
        baseUrl: 'http://127.0.0.1:8000',
        currentProject: null,
        loading: false,
        technologies: [],
    };
  },
  created() {
        this.loading = true;

        axios.get(`${this.baseUrl}/api/projects/${this.$route.params.slug}`)
            .then((resp) => {
            //controllo resp per vedere cosa ricevo
            console.log(resp);
            //salvo il project ricevuto
            this.currentProject = resp.data.result;
            this.technologies = this.currentProject.technologies;
            console.log(this.currentProject);
        }).finally(() =>{
            this.loading = false;
        });
    },
}

</script>

<template>
    <div class="container mt-3">
        <div v-if="loading">
            <h3>Loading...</h3>
        </div>
        <div v-else class="w-50">
            <h2>Title : {{ currentProject.title }} </h2>
            <p><strong>Project number : </strong> {{ currentProject.id }}</p>
            <p><strong>Type : </strong> {{ currentProject.type.name }}</p>
            <p><strong>Description : </strong> {{ currentProject.description }}</p>
        </div>
        <div>
            <strong>Technologies : </strong> 
            <p v-for="technology in technologies ">
                - {{ technology.name }}
            </p>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>