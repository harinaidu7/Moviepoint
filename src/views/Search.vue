<template>
    <div>
        <form  @submit.prevent = "handleSubmit" autocomplete="off">
            <div class="container-fluid py-5">
                <input type="text" v-model="query" @keyup="handleSubmit(query)"/>
            </div>
        </form>

        <div class="container-fluid d-flex">
            <div class="row text-center">
                <div class="col-sm-6 col-md-4 col-lg-3 p-3" v-for="items in data" :key="items.id">
                    <div class="card d-flex">
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


    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name:'Search',

        data(){
            return{
                query:'',
                data:[]
            }
        },

        methods:{
             async handleSubmit(query){
                let result= await axios.get('https://api.themoviedb.org/3/search/movie?api_key=5e999b2d6beaadc6a81d80f6bc17beb7&query=' + query)
                    this.data = result.data.results
                    console.log(this.data)
            
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
        background-color: #1f2833;
        height: 158px
    }
    .card{
        border: #0b0c10;
        
    }
    h1{
        color: #66fcf1
    }
    .navbar-toggler-icon{
        
        color:#1f2833
    }

</style>