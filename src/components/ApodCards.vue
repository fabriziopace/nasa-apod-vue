<template>
    <div class="container">
    <div class="row">
        <div v-for="d in dataPhoto" :key="d.url" class="card text-white bg-dark astronomy-card col-md-4">            
            <img :src="d.url" class="card-img-top" :alt="d.title">
             <div class="card-body">
                <h5 class="card-title">{{d.title}}</h5> 
                <!-- <p class="card-text">{{d.explanation}}</p> -->
                <p class="card-text"><small class="text-muted">{{d.date}}</small></p>
            </div> 
        </div>    
        <button class="btn btn-dark btn-show-more">Show more...</button>
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
        opacity: 0.9;
        max-height: 18rem;
    }
    
    .astronomy-card>img {
        max-height: 12rem;
        object-fit: cover;
    }
    
    .astronomy-card>.card-body>.card-title {
        font-size: 1rem;
    }
    
    .btn-show-more {
        margin: auto;
        margin-top: 2rem;
        margin-bottom: 2rem;
    }
</style>