<template>
    <div class="row">
        <div v-for="d in dataPhoto" :key="d.url" class="card text-white bg-dark astronomy-card col-md-4">            
            <img :src="d.url" class="card-img-top" :alt="d.title">
             <div class="card-body">
                <h5 class="card-title">{{d.title}}</h5> 
                <!-- <p class="card-text">{{d.explanation}}</p> -->
                <p class="card-text"><small class="text-muted">{{d.date}}</small></p>
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
        padding: 0;
        border-radius: 1%;
        opacity: 0.9;
        width: auto;
    }
    
    .card-title {
        font-size: 1rem;
    }
</style>