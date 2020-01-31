<template>
  <div class="container">
        <div v-for="d in dataPhoto" :key="d.url" class="card text-white bg-dark mb-3">            
            <img :src="d.url" class="card-img-top" :alt="d.title">
             <div class="card-body">
                <h5 class="card-title text-center">{{d.title}}</h5> 
            </div> 
        </div>
  </div>
</template>

<script>
    export default {
        props: ['dataPhoto']
    }
</script>

<style scoped>
    .astronomy-card {
        border-radius: 50%;
    }
</style>