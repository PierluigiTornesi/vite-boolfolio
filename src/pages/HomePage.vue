<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';

export default{
    data() {
        return {
            baseUrl: 'http://127.0.0.1:8000',
            projects: [],
        };
    },
    created() {
        axios.get(`${this.baseUrl}/api/projects`)
            .then((resp) => {
            //controllo resp per vedere cosa ricevo
            console.log(resp);
            //salvo i dati 
            this.projects = resp.data.results;
            //verifico che siano arrivati i dati
            console.log(this.projects);
        });
    },
    components: { ProjectCard }
}

</script>

<template>
    <div class="container mt-3">
        <h1 class="text-center">List of projects</h1>
        <div class="row row-cols-1 row-cols-md-3 row-cols-lg-4 g-3">
            <div class="col" v-for="project in projects" :key="project.id">
                <ProjectCard :project="project"/>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>
