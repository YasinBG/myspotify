<template>
  <div class="home">
    <div class="card relative">
      <router-link to="/movie/tt0409591" class="">
        <img
          src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/14e40a9c-be70-4c6a-8a94-bd4e8d71ffbb/d85l58y-11e48ee8-ea09-4684-8c34-7262da9c2a92.jpg/v1/fit/w_414,h_293,q_70,strp/naruto_by_xong_d85l58y-414w.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7ImhlaWdodCI6Ijw9NjM3IiwicGF0aCI6IlwvZlwvMTRlNDBhOWMtYmU3MC00YzZhLThhOTQtYmQ0ZThkNzFmZmJiXC9kODVsNTh5LTExZTQ4ZWU4LWVhMDktNDY4NC04YzM0LTcyNjJkYTljMmE5Mi5qcGciLCJ3aWR0aCI6Ijw9OTAwIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmltYWdlLm9wZXJhdGlvbnMiXX0.ZUBAKoMcI-H8BXLTcv559PleaMzwplevb_663giDWB8"
          alt=""
          class="block w-full h-[500px] object-cover"
        />

        <div class="bg-black detail absolute p-4 right-0 left-0 bottom-0 z-1 opacity-75">
          <h3 class="mb-4 font-semibold text-xl text-white">Naruto</h3>
          <p class="text-white">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima sit perspiciatis vero veniam deserunt rem reprehenderit, voluptatibus asperiores voluptate, atque nisi, tempora magnam illum pariatur ducimus deleniti quaerat in corporis!
          </p>
        </div>
      </router-link>
    </div>

    <form @submit.prevent="SearchMovies">
      <SearchInput v-model="search" class="py-5"></SearchInput>
      <input
        class="flex justify-center items-center flex-col p-4 mx-auto border bg-green-400 w-1/2 h-10 rounded-xl text-white font-bold text-2xl cursor-pointer"
        type="submit"
        value="Search"
      />
    </form>
  </div>
</template>

<script>
import SearchInput from "@/SearchInput.vue";
import { ref } from "vue";

export default {
  components: {
    SearchInput,
  },
  setup() {
    const search = ref("");

    const SearchMovies = () => {
      if (search.value !== "") {
        console.log(search.value);
      }
    };

    return {
      search,
      SearchMovies,
    };
  },
};
</script>

<style></style>
