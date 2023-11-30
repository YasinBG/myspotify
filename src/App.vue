<template>
  <div class="bg-gray-600 box-border">
  <header class="flex justify-center p-4 items-center bg-gray-600 shadow-md">
    <router-link to="/">
      <h1 class="text-white text-3xl font-serif shadow-lg"><span class="text-green-400">YBG</span>Movies</h1>

    </router-link>
  </header>
  <main>
  <router-view/>
</main>
</div>
</template>

<style>

body {
  background-color: rgb(41, 35, 35);
}

</style>
