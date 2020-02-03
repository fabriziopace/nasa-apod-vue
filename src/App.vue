<template>
    <div id="app">
        <ApodCards :dataPhoto="dataPhoto" class="align-self-center" />
        <div class="text-center py-3">
            <button class="btn btn-dark btn-show-more" @click="getPhotos">Show More...</button>
        </div>
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
                dataPhoto: [],
                startDate: moment()
            }
        },
        created: function () {
            this.getPhotos();
        },
        methods: {
            fetchApod: function (date) {
                let urlApi = 'https://api.nasa.gov/planetary/apod?api_key=' + process.env.VUE_APP_NASA_API_KEY + '&date=' + date;

                axios.get(urlApi)
                    .then((res) => {
                        res.data.date = moment(res.data.date).format('LLLL');
                        res.data.url = res.data.media_type === 'video' ? 'http://i3.ytimg.com/vi/' + res.data.url.toString().split('embed/')[1].split('?rel')[0] + '/hqdefault.jpg' : res.data.url;
                        this.dataPhoto.push(res.data);
                    });
            },
            getWeekDays: function () {
                let daysArray = [];
                let date = this.startDate;
                for (let d = 0; d < 9; d++) {
                    daysArray.push(date.format('YYYY-MM-DD'));
                    date.subtract(1, 'day');
                }
                date.subtract(1, 'day');
                return daysArray;
            },
            getPhotos: function () {
                let daysArray = this.getWeekDays();
                for (let d = 0; d < daysArray.length; d++) {
                    this.fetchApod(daysArray[d]);
                }
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

    [v-cloak] {
        display: none;
    }
</style>