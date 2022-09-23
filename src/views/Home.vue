<template>
    <div>
        <!-- navbar -->
        <nav class="navbar navbar-expand-lg py-3 ">
            <div class="container">

                <a href="#" class="navbar-brand">Moviepoint</a>
                <div class="search-div container-fluid d-flex"  @submit.prevent = "handleSubmit">
                    <i class="bi bi-search"></i>
                    <input class="search"  type="text" v-model="query" @keyup="handleSubmit(query)" spellcheck="false"/>
                </div>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navmenu"><span class="navbar-toggler-icon"></span></button>
                
                <div class="collapse navbar-collapse " id="navmenu">
                    <ul class="navbar-nav ms-auto" >
                        <li class="nav-item">
                            <a href="#Home" class="nav-link">Home</a>
                        </li>
                        <li class="nav-item">
                            <a href="#AboutUs" class="nav-link ">About Us</a>
                        </li>
                        <li class="nav-item">
                            <a href="#Contact" class="nav-link ">Contact</a>
                        </li>
                        <li class="nav-item">
                    
                        </li>
                    </ul>
                </div>
            </div>
            
        </nav>

        <!-- new nav -->



        <!-- discription -->
        <section>
            <div class="container py-5">
                <p class="disc">Moviepoint is an online database of information related to films, television series, home videos, video games, and streaming content online – including cast, production crew and personal biographies, plot summaries, trivia, ratings, and fan and critical reviews. Moviepoint began as a fan-operated movie database on the Usenet group "rec.arts.movies" in 1990, and moved to the Web in 1993. It is now owned and operated by Moviepoint.com, Inc., a subsidiary of Amazon.
        
                    As of March 2022, the database contained some 10.1 million titles (including television episodes) and 11.5 million person records. Additionally, the site had 83 million registered users. The site's message boards were disabled in February 2017.</p>
            </div>
        </section>

        <!-- <form  @submit.prevent = "handleSubmit" autocomplete="off">
            <div class="container-fluid py-5">
                <input type="text" v-model="query" @keyup="handleSubmit(query)"/>
            </div>
        </form> -->

        <!-- search results -->
        
        <div v-if="query">
            <h1 class="display-4 ">Search result</h1>
        </div>
        <div class="container-fluid d-flex" v-if="query">
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
        <section class="p-5" v-if="!query" >

        <!-- header   -->
            <div >
                <h1 class="display-4 ">Popular Movies</h1>
            </div>
        <!-- header end-->

        <!-- working modal -->
        <div v-for="(items) in data" :key="items.id">
          <!-- <b-button v-b-modal.modal-1>Launch demo modal</b-button> -->
          <b-modal id="modal-1" title="Overview">
            <p  class="my-4">{{items.overview}}</p>
          </b-modal>
        </div>
        <!-- working modal end -->

        <!-- movie card -->
            <div class="container-fluid d-flex">
                <div class="row text-center">
                    <div class="col-sm-6 col-md-4 col-lg-3 p-3" v-for="items in data" :key="items.id">
                        <div class="card d-flex" >

                          <!-- Modal -->
                         
                          
                          <!-- Modal -->
                         
                          
                         

                          
                           
                          <!-- modal end -->
                            <div class="poster">
                                <img class="card-img-top" :src="'http://image.tmdb.org/t/p/w500/'+items.poster_path" alt="Card image cap"/>
                            </div>
                            <div class="card-content">
                                <div class="title px-3 pt-3">
                                    <h5 class="card-title">{{items.title}}</h5>
                                </div>
                                <div class="d-flex flex-row" >
    
                                    <div class="release-date d-flex flex-column text-left p-3 " >
                                        <div>Release date</div>
                                        <div class="date">{{items.release_date}}  <b-button class="button" v-b-modal.modal-1 >more</b-button>
                                          <!-- <b-modal id="modal-1" title="BootstrapVue">
                                            <p  class="my-4">{{this.data.overview}}</p>
                                          </b-modal> -->
                                        </div>
                                        
                                    </div>
                                    <div class="rating p-3">
                                      <div class="rating" >Rating</div>
                                      <div class="d-flex">
                                        <div class="star"><i id="star" class="bi bi-star-fill" @click="toggle1"></i></div> 
                                        <div class="rating-num">{{items.vote_average}}</div> 
                                      </div>
                                    </div>
                                  </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
          <!-- movie card end -->  
        </section>

       

        


    </div>
</template>

<script>
import axios from "axios";
import Search from "./Search.vue";

export default {
  name: "Home",

  data() {
    return {
      data: [],
      query: "",
      list: [],
      star: " ",
      bodyBgVariant: "dark",
      // showModal: true,
      // OpenClose: true
      show: true,
    };
  },

  mounted() {
    this.getData();
  },
  methods: {
    async getData() {
      let result = await axios.get(
        "https://api.themoviedb.org/3/movie/popular?api_key=5e999b2d6beaadc6a81d80f6bc17beb7&language=en-US&page=1"
      );
      console.log(result.data);
      this.data = result.data.results;
      this.disc = result.data.results[20].overview
      console.log(this.disc) 
      this.dataFetched = true;
    },
    async handleSubmit(query) {
      if (!query) {
        console.log("query", query);
        await this.getData();
      } else {
        let result = await axios.get(
          "https://api.themoviedb.org/3/search/movie?api_key=5e999b2d6beaadc6a81d80f6bc17beb7&query=" +
            query
        );
        this.data = result.data.results;
        console.log(this.data);
      }
    },
    toggle1() {
      if (star.style.color == "white") {
        star.style.color = "yellow";
      } else {
        star.style.color = "white";
      }
    },
    toggleModel() {
      this.showModel = !this.showModel;
    },
    OpenClose() {
      this.show = !this.show;
    },
  },
  // watch:{
  //   visible: function(newVal,oldVal){
  //     this.OpenClose = newVal
  //     console.log('new'+ newVal + '==' + oldVal)
  //   }
  // }
};
</script>

<style scoped>
.title {
  text-align: left;
  color: #45a29e;
}
.release-date {
  text-align: left;
  color: #c5c6c7;
}
.date {
  color: black;
}
.navbar {
  background-color: #0b0c10;
  color: #66fcf1;
}
.navbar-brand {
  color: #66fcf1;
}
.nav-link {
  color: #66fcf1;
}
.disc {
  color: #c5c6c7;
}
.card-content {
  background-color: #1f2833;
  height: 230px;
}
.card {
  border: #0b0c10;
  cursor: pointer;
}
h1 {
  color: #66fcf1;
}
.navbar-toggler-icon {
  color: #1f2833;
}
.rating {
  color: #c5c6c7;
}
.star {
  padding-right: 5px;
}
.rating-num {
  font-size: 17px;
}
.search {
  width: 100%;
  border: 0px;
  background-color: #1f2833;
  color: #c5c6c7;
}
i {
  background-color: #1f2833;
  border: 0px;
}
.search-div {
  background-color: #1f2833;
  width: 65%;
  border-radius: 27px;
}
textarea:focus,
input:focus {
  outline: none;
}
.modal-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 98;
  background-color: rgba(194, 2, 2, 0.3);
}
.fade-enter-action,
.fade-leave-action {
  transition: opacity 10s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 99;

  width: 100%;
  max-width: 400px;
  background-color: #fff;
  border-radius: 16px;

  padding: 25px;
}
.button {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;

  display: inline-block;
  background-image: linear-gradient(to right, #cc2e5d, #ff5858);
  border-radius: 8px;

  color: #fff;
  font-size: 18px;
  font-weight: 700;
}
section {
  background-color: #000000;
}

</style>