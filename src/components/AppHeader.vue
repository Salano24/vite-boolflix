<script>
import axios from 'axios';
import { state } from '../state.js';
    export default{
        name: "AppHeader",
        data(){
            return{
                state
            }
        },
        methods: {
            log(){
                console.log(this.state.searchText)
                this.state.url = `https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=${this.state.searchText}`
                this.state.searchText = ""
                axios.get(this.state.url)
                .then(response => {
                    this.state.entries = response.data.results
                    this.state.info = response.data.info
                    console.log(response.data.results)
                    console.log(this.state.entries)
                })
            }
        }
    }
</script>

<template>
    <div class="headerWrapper">
        <h1 class="title text-white">BoolFlix</h1>
        <div class="searchbar">
            <input type="text" placeholder="Write a film title..." v-model="state.searchText">
            <button class="" v-on:click="log()">Search</button>
        </div> 

      </div>
      <h2>BOOTFLIX ORIGINALS</h2>
</template>

<style>
 .title{
  color:#e50914 ;
  font-size: 4rem;
 }
input{
  padding: 0.5rem 1rem;
  font-weight: 700;
  font-family: Netflix Sans,Helvetica Neue,Segoe UI,Roboto,Ubuntu,sans-serif;

}

h2{
  color: white;
  width: 80%;
  margin: auto;
  padding-bottom: 2rem;
}
 button{
  background-color: #e50914;
 padding: 0.75rem 1rem;
 margin-left: 1rem;
 font-weight: 800;
  border: 0;
  font-family: Netflix Sans,Helvetica Neue,Segoe UI,Roboto,Ubuntu,sans-serif;
 }

 .searchbar{
  display: flex;
  align-items: center;
 }

 .headerWrapper{
margin: auto;
  display: flex;
 justify-content: space-between;
 align-items: center;
  width: 80%;
  padding: 3rem 0;
  
 }
</style>
