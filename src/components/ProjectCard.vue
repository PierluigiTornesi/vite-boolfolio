<script>

export default{
    props:{
        project: Object,
      },
    data(){
    return{
        
    }
  },methods: {
    truncateText(text){
        if(text && text.length > 200){
            return text.substring(0, 150) + '...';
        }
        return text;
    }
  },
}

</script>

<template>
    <div class="card h-100" style="width: 18rem;">
        <div class="card-body">
          <h5 class="card-title mb-3">Title : {{ project.title }}</h5>
          <h6 class="card-subtitle mb-3 text-body-secondary"><strong>Slug :</strong> {{ project.slug}}</h6>
          <p class="card-text"><strong>Description :</strong> {{ project.description ? truncateText(project.description) : "No description available"}}</p>
          
          <router-link :to="{name: 'show-project', params: {slug: project.slug}}" class="btn btn-success">Details</router-link>
        </div>
     </div>
</template>

<style lang="scss" scoped>

</style>
