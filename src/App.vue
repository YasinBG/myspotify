<template>
  <body>
  <div class="bg-gray-600 box-border ">
  <header class="flex justify-center mx-3 my-4 p-4 items-center bg-gray-600 shadow-md">
    <router-link to="/" class="">
      <h1 class=" text-white text-3xl text-center p-6 font-serif shadow-lg"><span class="text-green-400 ">YBG</span> Movies</h1>
       <home-view></home-view>
    </router-link>
  </header>
  <main>
  <router-view/>
</main>
</div>
</body>
</template>
<script>
import HomeView from './views/HomeView.vue';
export default {
  components:{
    HomeView
  },
  setup(){

    return {

    }
  }
}
</script>

<style>

body {
  background-color: rgb(41, 35, 35);
}

</style>
