<template>
    <div>
        <!-- navbar -->
        <nav class="navbar navbar-expand-lg py-3">
            <div class="container">

                <a href="#" class="navbar-brand">Moviepoint</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navmenu"><span class="navbar-toggler-icon"></span></button>
                
                <div class="collapse navbar-collapse " id="navmenu">
                    <ul class="navbar-nav ms-auto" >
                        <li class="nav-item">
                            <a href="#Home" class="nav-link">Home</a>
                        </li>
                        <li class="nav-item">
                            <a href="#AboutUs" class="nav-link">About Us</a>
                        </li>
                        <li class="nav-item">
                            <a href="#Contact" class="nav-link">Contact</a>
                        </li>
                    </ul>
                </div>
            </div>
            
        </nav>

        <!-- discription -->
        <section>
            <div class="container py-5">
                <p class="disc">Moviepoint is an online database of information related to films, television series, home videos, video games, and streaming content online – including cast, production crew and personal biographies, plot summaries, trivia, ratings, and fan and critical reviews. Moviepoint began as a fan-operated movie database on the Usenet group "rec.arts.movies" in 1990, and moved to the Web in 1993. It is now owned and operated by Moviepoint.com, Inc., a subsidiary of Amazon.
        
                    As of March 2022, the database contained some 10.1 million titles (including television episodes) and 11.5 million person records. Additionally, the site had 83 million registered users. The site's message boards were disabled in February 2017.</p>
            </div>
        </section>

        <!-- Movies section -->

        <!-- <section class="p-5">
            <div class="container-fluid" >
                <div class="row p-0 m-0 text-center g-4">
                    <div class="col-sm-6 col-md-4 col-lg-3" v-for="items in data" :key="items.id">
                        <div class="card" style="width: 18rem;">
                            <img class="card-img-top" :src="'http://image.tmdb.org/t/p/w500/'+items.poster_path" alt="Card image cap">
                            <div class="card-body">
                              <h5 class="card-title">{{items.title}}</h5>
                              <p class="card-text"></p>
                              <a href="#" class="btn btn-primary">Go somewhere</a>
                            </div>
                          </div>
                    </div>
                </div>


            </div>
        </section> -->

        <!-- top movies -->
        <section class="p-5">
            <div class="container-fluid">
                <div class="row text-center">
                    <div class="col-sm-6 col-md-4 col-lg-3 p-3" v-for="items in data" :key="items.id">
                        <div class="card">
                            <div class="poster">
                                <img class="card-img-top" :src="'http://image.tmdb.org/t/p/w500/'+items.poster_path" alt="Card image cap"/>
                            </div>
                            <div class="card-content">
                                <div class="title px-3 pt-3">
                                    <h5 class="card-title">{{items.title}}</h5>
                                </div>
                                <div class="d-flex flex-row">
    
                                    <div class="release-date d-flex flex-column text-left p-3 ">
                                        <div >Release date</div>
                                        <div class="date">{{items.release_date}}</div>
                                    </div>
                                    <div class="rating p-3">
                                        <div >Rating</div>
                                        <div>
                                            {{items.vote_average}}
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                        </div>
                    </div>
                </div>
            </div>
        </section>

        


    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: 'Home',
        data(){
            return{
                data:[]
            }
        },

        mounted() {
            this.getData();
        },

        methods:{
           async getData(){
                let result= await axios.get("https://api.themoviedb.org/3/movie/popular?api_key=5e999b2d6beaadc6a81d80f6bc17beb7&language=en-US&page=1");
                console.log(result.data)
                this.data= result.data.results
            },
        }
    }
</script>

<style scoped>
    .title{
        text-align: left;
        color: #45a29e
    }
    .release-date{
        text-align: left;
        color:#c5c6c7
    }
    .date{
        color: black
    }
    .navbar{
        background-color: #0b0c10;
        color: #66fcf1 
    }
    .navbar-brand{
        color: #66fcf1
    }
    .nav-link{
        color: #66fcf1
    }
    .disc{
        color:#c5c6c7
    }
    .card-content{
        background-color: #1f2833
    }
    .card{
        border: #0b0c10
    }
</style>