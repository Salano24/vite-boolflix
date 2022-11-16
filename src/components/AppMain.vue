<script>
    import {state} from "../state.js"
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
            <div class="col-3" v-for="(entry,i) in state.entries">
                <img class="movie-img" :src="state.path+entry.poster_path" :alt="entry.title">
                <div class="movie-info ">
                    <p><span class="movie-property">Title:</span> {{entry.title}}</p>
                    <p><span class="movie-property"> Original title:</span> {{entry.original_title}}</p>
                    <div>
                        <span class="movie-property">Lenguage: <span class="language">{{entry.original_language}}                         <img :src="state.imgPath+'/'+entry.original_language+'.png'" alt="" class="lang-flag"></span></span>
                    </div>
                   
                    <p><span class="movie-property">Description:</span> {{entry.overview}}</p>
                </div>
            </div>

        </div>
    </div>
        
</template>

<style lang="scss" scoped>
        
   .movie-img{
    height: 300px;
    margin-left: 1rem;
   }
    .movie-info>*{
        margin: 1rem;
    }
    

        .language{
            text-transform:uppercase
        }
        .lang-flag{
            width: 2.5rem;
        
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