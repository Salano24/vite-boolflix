<script >
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import AppFooter from './components/AppFooter.vue'
import axios from 'axios'
export default {
    name: 'App',
    components: {
        AppHeader,
        AppMain,
        AppFooter
    },
     data(){
      return{

      }
     },
     mounted(){
      const config = {
        method: 'get',
        url: 'https://api.themoviedb.org/3/search/movie',
        params:{
          api_key: '1b32ddfb907479d3f1925c29e2e15ca2',
          query: 'Matrix'
        }
      };
      axios(config)
      .then(function (response){
        console.log(response.data);

      })
      .catch(function (error) {
        console.log(error);
        
      })
     }
    
}
</script>

<template>
 
</template>

<style scoped>

</style>
