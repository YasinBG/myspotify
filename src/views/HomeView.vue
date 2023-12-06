<template>
  
    <div class="card relative">
      <router-link to="/movie/tt3896198" class="">
        <img
          src="https://cdn.anisearch.com/images/character/cover/0/29_300.webp"
          alt=""
          class="block w-full h-[500px] object-cover relative z-0"
        />

        <div class="bg-black detail absolute p-4 right-0 left-0 bottom-0 z-1 opacity-75">
          <h3 class="mb-4 font-semibold text-xl text-white">Naruto</h3>
          <p class="text-white">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima sit perspiciatis vero veniam deserunt rem reprehenderit, voluptatibus asperiores voluptate, atque nisi, tempora magnam illum pariatur ducimus deleniti quaerat in corporis!
          </p>
        </div>
      </router-link>
    </div>

    <form @submit.prevent="searchMovies()" class="flex flex-col p-5 justify-center">
      <input type="text"  class="w-3/4 mx-auto h-10  text-lg text-gray-900 border border-gray-300 rounded-lg bg-gray-50"  placeholder="  search" v-model="search"/>
      
      <input
        class=" my-5 uppercase mx-auto border bg-green-400 w-1/2 h-10 rounded-xl text-white font-bold text-2xl cursor-pointer"
        type="submit"
        value="Search"
      />
    </form>
    <div v-for="movie in movies" :key="movie.imdbID">
      
      <router-link :to="'/movie/' + movie.imdbID">

        <div>
          <img :src="movie.Poster" alt="">
          <div>{{ movie.Type }}</div>
        </div>

      </router-link>
    </div>

</template>

<script>

import { ref } from 'vue';
import env from '@/env.js'


export default {
  components: {
    
  },
  setup() {
    const search = ref("");

    const movies = ref([])

    const searchMovies = () => {
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
         .then(response => response.json())
         .then(data => {
          movies.value = data.Search;
          search.value = "";
          
         })
      }
    
  }
      
  

    return {
      search,
      searchMovies,
      movies
    };
  },
};
</script>

<style></style>
