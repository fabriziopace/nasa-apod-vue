<template>
  <div id="app" class="container">
      <div class="row">
      <ApodCards :dataPhoto="dataPhoto" class="align-self-center" />
    </div>
  </div>
</template>

<script>
    import ApodCards from './components/ApodCards.vue';
    import axios from 'axios';

    export default {
        name: 'app',
        components: {
            ApodCards
        },
        data() {
            return {
                dataPhoto: []
            }
        },
        created: function() {
            this.fetchApod();
        },
        methods: {
            fetchApod: function() {
                let urlApi = 'https://api.nasa.gov/planetary/apod?api_key=' + process.env.VUE_APP_NASA_API_KEY;

                axios.get(urlApi)
                    .then((res) => {
                        this.dataPhoto.push(res.data);
                    });
            }
        }
    }
</script>

<style>
    body {
        background-color: rgb(40, 40, 40);
    }
    
    .container {
        display: flex;
        align-items: center;
        flex-direction: row;
        justify-content: center;
    }
    
    .row {
        height: 100vh;
    }
    
    [v-cloak] {
        display: none;
    }
</style>