<template>
  <div>
    <!-- WeatherApp bileşeni -->
    <h1>Hava Durumu Günlükleri</h1>
    <div v-for="dailyWeather in weatherData.result" :key="dailyWeather.date">
      <!-- ... (hava durumu bilgileri için gerekli HTML) -->
    </div>

    <div class="container mx-auto p-4">
      <!-- MovieList bileşeni -->
      <h1 class="text-3xl font-bold mb-4">Film Listesi</h1>
      <div v-for="movie in movies" :key="movie.id" class="flex mb-4">
        <!-- ... (film bilgileri için gerekli HTML) -->
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import axios from 'axios';

export default {
  name: 'CombinedApp',
  setup() {
    // WeatherApp bileşeni
    const weather = ref(null);
    const error = ref(null);

    const fetchData = async () => {
      try {
        const response = await axios.get("https://api.collectapi.com/weather/getWeather", {
          params: {
            "data.lang": "tr",
            "data.city": "ankara"
          },
          headers: {
            'content-type': 'application/json',
            'authorization': 'apikey your_token'
          }
        });

        console.log(response.data);

        weather.value = {
          city: response.data.result.city,
          description: response.data.result.description,
          temperature: response.data.result.temperature,
          updateTime: response.data.result.updateTime
        };
      } catch (error) {
        console.error('Hava durumu verilerini getirme hatası:', error);
        error.value = 'Hava durumu verilerini getirme hatası';
      }
    };

    const formatTime = (time) => {
      const date = new Date(time);
      return `${date.getHours()}:${String(date.getMinutes()).padStart(2, '0')}`;
    };

    onMounted(() => {
      fetchData();
    });

    const updateWeather = async () => {
      try {
        await fetchData();
        console.log("Hava durumu başarıyla güncellendi.");
      } catch (error) {
        console.error('Hava durumu güncelleme hatası:', error);
      }
    };

    // MovieList bileşeni
    const movies = ref([]);

    // Film verilerini API'den al
    // ...

    // Sayfa yüklendiğinde film verilerini al
    // ...

    return {
      weather,
      error,
      updateWeather,
      formatTime,
      movies,
    };
  },
};
</script>

<style>
/* Gerekirse stil tanımlamaları eklenebilir */
</style>
