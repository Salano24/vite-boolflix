<script>
    import {state} from "../state.js"
    import '../../node_modules/@fortawesome/fontawesome-free'
    export default {
        name: "AppMain",
        data() {
            return{
                state
            }
        },
        mounted(){
        },
        methods: {
        },
        computed: {
            
        }
    }
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-3 movie-card" v-for="(entry,i) in state.entries">
                <div class="movie-info hidden">
                    <p class="movie-title"><span class="movie-property">Title:</span> {{entry.title}}</p>
                    <p><span class="movie-property"> Original title:</span> {{entry.original_title}}</p>
                    <div>
                        <span class="movie-property">Lenguage:<span class="language">{{entry.original_language}}                         <img :src="state.imgPath+'/'+entry.original_language+'.png'" alt="" class="lang-flag"></span></span>
                    </div>
                   
                    <p class="description"><span class="movie-property">Description:</span> {{entry.overview}}</p>
                    <div class="movie-rating justify-content-center">
                            <p v-for="index in Math.round(entry.vote_average / 2)">
                                <i class="fa-solid fa-star"></i>
                            </p> 
                            <p v-for="index in 5-Math.round(entry.vote_average / 2)">
                                <i class="fa-regular fa-star"></i>
                            </p>
                        </div>
                </div>
                <img class="movie-img" :src="state.path+entry.poster_path" :alt="entry.title">

            </div>

        </div>
    </div>
        
</template>

<style lang="scss" scoped>


     
     .movie-title{
        font-size: 2rem;
        color: #e50914;
     }



     .description {
        font-size: 0.6rem;
        margin-top:1rem ;

     }

     
    

    .hidden{
        top: 0;
        left: 0;
        position: absolute; 
        opacity: 0;
    }

    .movie-card:hover .movie-img{
        opacity: 0;
    }

    .movie-card:hover .movie-info{
        opacity: 1;
    }

    

    .movie-card{
        position: relative;
        margin-bottom: 1rem;
    }

    .movie-img:hover {
        display: none;
    }
   .movie-img{
    margin-left: 1rem;
   }
    .movie-info .language{
        margin: 1rem;
        font-size: 0.75rem;
    }

    .movie-info{
        background-color: #222222;
        border: 5px solid #e50914;
        padding: 0.5rem;
        box-shadow: 5px 5px 5px  white;


        

    }

    .movie-info, .movie-img{
        height: 380px;
        width: 260px;
    }
    

        .language{
            text-transform:uppercase;
        }
        .lang-flag{
            width: 1rem;
        
        }
    

    .row{
        display: flex;
        color: white;
        flex-wrap: wrap;
        font-weight: 600;
    }

    .col-3{
        width: calc(100% / 12 * 3);
    }

    .container{
        width: 80%;
        margin: auto;
    }
</style>