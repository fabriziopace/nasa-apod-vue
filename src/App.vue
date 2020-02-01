<template>
  <div id="app" class="container">
      <ApodCards :dataPhoto="dataPhoto" class="align-self-center" />
  </div>
</template>

<script>
    import ApodCards from './components/ApodCards.vue';
    import axios from 'axios';
    import moment from 'moment';

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
            let daysArray = this.getWeekDays();
            for (let d = 0; d < daysArray.length; d++) {
                this.fetchApod(daysArray[d]);
            }
        },
        methods: {
            fetchApod: function(date) {
                if (!date) {
                    date = moment().format('YYYY-MM-DD')
                }
                let urlApi = 'https://api.nasa.gov/planetary/apod?api_key=' + process.env.VUE_APP_NASA_API_KEY + '&date=' + date;

                axios.get(urlApi)
                    .then((res) => {
                        this.dataPhoto.push(res.data);
                    });
            },
            getWeekDays: function() {
                let daysArray = [];
                let date = moment().isoWeek(1).startOf('week');
                for (let d = 0; d < 7; d++) {
                    daysArray.push(date.format('YYYY-MM-DD'));
                    date.add(1, 'day');
                }
                return daysArray;
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