<template>
    <div class="container">
        <div class="row">
            <div v-for="(d, index) in dataPhoto" :key="d.url" class="astronomy-card col-md-4" data-toggle="modal"
                data-target="#astronomy-modal">
                <img :src="d.url" class="card-img-top" :alt="d.title" data-target="#astronomy-carousel" :index="index"
                    :data-slide-to="index">
            </div>
        </div>

        <div class="modal fade" id="astronomy-modal" tabindex="-1" role="dialog" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-body">
                        <div id="astronomy-carousel" class="carousel" data-ride="carousel">
                            <div class="carousel-inner">
                                <div v-for="(d, index) in dataPhoto" :key="d.url"
                                    :class="index === 0 ? 'carousel-item active' : 'carousel-item'">
                                    <img class="d-block w-100" :src="d.url">
                                </div>
                            </div>
                            <a class="carousel-control-prev" href="#astronomy-carousel" role="button" data-slide="prev">
                                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                                <span class="sr-only">Previous</span>
                            </a>
                            <a class="carousel-control-next" href="#astronomy-carousel" role="button" data-slide="next">
                                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                                <span class="sr-only">Next</span>
                            </a>
                        </div>
                    </div>
                </div>
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
        padding: 0px;
        opacity: 0.8;
        cursor: pointer;
    }

    .astronomy-card:hover {
        opacity: 1;
    }

    .astronomy-card>img {
        object-fit: cover;
        height: 40vw;
    }

    @media (min-width: 768px) {
        .astronomy-card>img {
            height: 25vw;
        }
    }
    @media (min-width: 992px) {
        .astronomy-card>img {
            height: 18vw;
        }
    }

    .carousel-item>.img {
        height: 60vh;
        object-fit: cover;
    }

    @media (min-width: 576px) {
        .carousel-item>.img {
            height: 350px;
        }
    }
</style>