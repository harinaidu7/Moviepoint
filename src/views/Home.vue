<template>
    <div>
        <!-- navbar start -->
        <nav class="navbar navbar-expand-lg py-3 ">
            <div class="container">
             <!-- navbar brand  -->
                <a href="#" class="navbar-brand">Moviepoint</a>
             <!-- navbar brand end-->
             <!-- search bar start -->
                <div class="search-div container-fluid d-flex"  @submit.prevent = "handleSubmit">
                    <i class="bi bi-search"></i>
                    <input class="search"  type="text" v-model="query" @keyup="handleSubmit(query)" spellcheck="false"/><button class="search-button"><a href="#container" v-smooth-scroll>enter..</a></button>
                </div>
             <!-- search bar end -->
             <!-- navbar toggle-button-->
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navmenu"><span class="navbar-toggler-icon"></span></button>
             <!-- navbar toggle-button end-->
             <!-- search bar elements -->
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
             <!-- search bar elements -->  
            </div>
        </nav>
        <!--navbar end -->

        <!-- banner -->

        <!-- <section class="hero">
          
          <h2>{{this.random.title}}<br/>
            <h4 class="banner-disc">{{this.random.overview}}</h4>
            
            <div class="d-flex p-2">
              <div class="col d-flex px-1">
                <i class="bi bi-play"> play</i>
                <button class="banner-button">More</button>
              </div>
            </div>
          </h2>
          
        </section> -->

        <!-- banner end -->

        <!-- working banner -->
        <section class="banner-1" v-if="!query">
          <div class="container-fluid p-0 banner-1">
            <!-- <div class="d-flex align-item-center justify-content-between"> -->
              <!-- banner img -->
              <img class="banner" :src="'http://image.tmdb.org/t/p/w500/'+this.random.backdrop_path" /> 
              <!-- banner img end -->
              <!-- banner header and overview       -->
              <div class="text-block">
                <h2>{{this.random.title}}</h2>  <!--  title-->
                <p>{{this.random.overview}}</p> <!--  overview-->
                <div class="d-flex flex-row">
                  <div class="d-flex px-3">
                    <button class="button button-play bi bi-play py-3 px-4">PLAY</button> <!-- play button  -->
                  </div>
                  <div>
                    <button class="button button-more py-3 px-4">MORE</button>  <!-- more button  -->
                  </div>
                </div>
              </div>
              <!-- banner header and overview end-->
            <!-- </div> -->
          </div>
        </section>
        <!-- working banner end -->




        <!-- discription -->
        <!-- <section>
          <div class="container-fluid py-5">
            <p class="disc">Moviepoint is an online database of information related to films, television series, home videos, video games, and streaming content online – including cast, production crew and personal biographies, plot summaries, trivia, ratings, and fan and critical reviews. Moviepoint began as a fan-operated movie database on the Usenet group "rec.arts.movies" in 1990, and moved to the Web in 1993. It is now owned and operated by Moviepoint.com, Inc., a subsidiary of Amazon.
    
                As of March 2022, the database contained some 10.1 million titles (including television episodes) and 11.5 million person records. Additionally, the site had 83 million registered users. The site's message boards were disabled in February 2017.
            </p>
          </div>
        </section> -->
        <!-- discription end -->


        <!-- search results -->
        <section>
          <!-- header -->
          <div class="container-fluid p-0" v-if="query">
              <h1 class="display-4">Search result</h1>
          </div>
          <!-- header end -->

         <!-- working modal -->
         <div class="container-fluid d-flex" id="container">

          <div class="d-flex flex-row text-center">
            <div class="col-sm-6 col-md-4 col-lg-3 p-3">
              <b-modal size="md" id="modal-1" :title = 'this.title'>
                <div class="d-flex flex-column">
                  <div class="container p-0">
                    <img class="poster-modal" :src="'http://image.tmdb.org/t/p/w500/'+this.poster" />
                  </div>
                  <div>
                    <p  class="overview-modal my-4">{{this.para}}</p>
                  </div>
                </div>
              </b-modal>
            </div>
          </div>
                    
        </div>
        <!-- working modal end -->
        <div class="container-fluid d-flex search-body" v-if="query">
            <div class="row text-center">
                <div class="col-sm-6 col-md-4 col-lg-3 p-3" v-for="item in data" :key="item.id">
                    <div class="card d-flex">
                        <div class="poster">
                            <img class="card-img-top" :src="'http://image.tmdb.org/t/p/w500/'+item.poster_path" alt="Card image cap"/>
                        </div>
                        <div class="card-content">
                            <div class="title px-3 pt-3">
                                <h5 class="card-title">{{item.title}}</h5>
                            </div>
                            <div class="d-flex flex-row">

                                <div class="release-date d-flex flex-column text-left p-3 ">
                                    <div >Release date</div>
                                    <div class="date">{{item.release_date}}</div>
                                    <div class="col">
                                      <b-button class="button" v-b-modal.modal-1 @click="itemClicked(item)" >more</b-button>
                                    </div>
                                </div>
                                <div class="rating p-3">
                                    <div >Rating</div>
                                    <div>
                                        {{item.vote_average}}
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
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
        <section  v-if="!query" >

        <!-- header   -->
            <div >
                <h1 class="display-4 ">Popular Movies</h1>
            </div>
        <!-- header end-->

        <!-- working modal -->
        <div class="container-fluid d-flex">
          <div class="d-flex flex-row text-center">
            <div class="col-sm-6 col-md-4 col-lg-3 p-3">
              <b-modal size="md" id="modal-1" :title = 'this.title'>
                <div class="d-flex flex-column">
                  <div class="container p-0">
                    <img class="poster-modal" :src="'http://image.tmdb.org/t/p/w500/'+this.poster" />
                  </div>
                  <div>
                    <p  class="overview-modal my-4">{{this.para}}</p>
                  </div>
                </div>
              </b-modal>
            </div>
          </div>
          <!-- <b-button v-b-modal.modal-1>Launch demo modal</b-button> -->
        </div>
        <!-- working modal end -->

        <!-- movie card -->
            <div class="container-fluid d-flex">
                <div class="row text-center">
                    <div class="col-sm-6 col-md-4 col-lg-3 p-3" v-for="item in data" :key="item.id">
                        <div class="card d-flex" >
                            <div class="poster">
                                <img class="card-img-top" :src="'http://image.tmdb.org/t/p/w500/'+item.poster_path" alt="Card image cap"/>
                            </div>
                            <div class="card-content">
                                <div class="title px-3 pt-3">
                                    <h5 class="card-title">{{item.title}}</h5>
                                </div>
                                <div class="d-flex flex-row" >
    
                                    <div class="release-date d-flex flex-column text-left p-3 " >
                                        <div>Release date</div>
                                        <div class="date">{{item.release_date}} 
                                          <div class="col">
                                            <b-button class="button" v-b-modal.modal-1 @click="itemClicked(item)" >more</b-button>
                                          </div>
                                          <!-- <b-modal id="modal-1" title="BootstrapVue">
                                            <p  class="my-4">{{this.data.overview}}</p>
                                          </b-modal> -->
                                        </div>
                                        
                                    </div>
                                    <div class="rating p-3">
                                      <div class="rating" >Rating</div>
                                      <div class="d-flex">
                                       <div class="star"><i id="star" class="bi bi-star-fill" @click="toggle1"></i></div> 
                                        <div class="rating-num">{{item.vote_average}}</div> 
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
      star: " ",
      bodyBgVariant: "dark",
      // showModal: true,
      // OpenClose: true
      show: true,
      para: "",
      title: "",
      random: "",
    };
  },

  mounted() {
    this.randomMovie();
    this.getData();
    this.itemClicked();
  },
  methods: {
    async getData() {
      let result = await axios.get(
        "https://api.themoviedb.org/3/movie/popular?api_key=5e999b2d6beaadc6a81d80f6bc17beb7&language=en-US&page=1"
      );
      console.log(result.data);
      this.data = result.data.results;
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
          console.log(result)
        
      }
    },

    itemClicked(item) {
      this.para = item.overview;
      this.poster = item.backdrop_path;
      this.title = item.title;
      console.log(this.para);
      $("#modal-1").modal("show");
    },

    async randomMovie() {
      let randomNum = Math.floor(Math.random() * 100);
      let result = await axios.get(
        "https://api.themoviedb.org/3/discover/movie?api_key=5e999b2d6beaadc6a81d80f6bc17beb7&language=en-US&include_adult=false&with_genres=28&page=" +
          randomNum
      );
      this.random = result.data.results[0];
      console.log(this.random);
    },

    scrollToElement() {
      const container = this.$refs.scrollToMe("#container");
      container.scrollTop = container.scrollHeight;
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
body {
  background-color: #000000;
}
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
  background-color: #000000;
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
.poster-modal {
  height: inherit;
  width: inherit;
  padding: inherit;
}

/deep/.modal-content {
  background-color: #1f2833;
  color: #66fcf1;
  padding: 2px;
}

/deep/.overview-modal {
  padding: inherit;
  padding: 10px;
}

/deep/.modal-header {
  border-bottom: none;
}

/deep/.modal-footer {
  border-top: none;
}

/deep/ .modal-body {
  padding: 0;
}

.hero {
  width: 100%;
  height: 500px;
  background-color: greenyellow;
  /* background-image: url('../assets/movie-1.jpg');*/
  background-position: center;
  position: relative;
}

.hero > h2 {
  font-size: 3rem;
  color: #fff;
  text-align: left;
  padding-top: 120px;
  font-weight: bold;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 500px;
  background-image: linear-gradient(
    to right,
    rgba(0, 0, 0, 1) 20%,
    rgba(0, 0, 0, 7) 40%,
    rgba(0, 0, 0, 0) 100%
  );
}

.hero > h4 {
  font-size: 3rem;
  color: #fff;
  text-align: left;
  padding-top: 120px;
  font-weight: bold;
}
h4 {
  padding-top: 20px;
  font-weight: 100;
}
.banner-button {
  font-size: 30px;
  padding-left: 13px;
  border-radius: 10px;
  text-align: center;
  background-color: #f2f3f77b;
  color: #fff;
}
/*.bi-play{
 font-size:33px;
 border-radius: 10px;
 background-color: #f2f3f77b;
 text-align: center
}*/
.banner {
  width: 100%;
  height: 450px;
  background-color: linear-gradient(
    to right,
    rgba(0, 0, 0, 1) 20%,
    rgba(0, 0, 0, 7) 40%,
    rgba(0, 0, 0, 0) 100%
  );
}
.text-block {
  position: absolute;
  bottom: 100px;
  right: 20px;
  background-color: rgba(0, 0, 0, 0.197);
  color: white;
  padding-left: 20px;
  padding-right: 20px;
  background-image: linear-gradient(
    to right,
    rgba(0, 0, 0, 1) 20%,
    rgba(0, 0, 0, 7) 40%,
    rgba(0, 0, 0, 0) 100%
  );
  text-align: left;
}
.search-body {
  background-color: #000000;
}
.display-4 {
  background-color: #000000;
}
.search-button {
  background-color: #1f2833;
  border-width: 0px;
}
a {
  text-decoration: none;
}
</style>