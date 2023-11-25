<template>
  <div class="about">
    <h1>This is the movies view</h1>
  </div>
</template>
 <template>
  <carousel :items-to-show="5">
    <slide v-for="movie in latestReleases" :key="movie">
      {{ movie }}
    </slide>

    <template #addons>
      <navigation />
      <pagination />
    </template>
  </carousel>
</template>

<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

export default {
  name: 'App',
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
      latestReleases: ['movie1', 'movie2'],
      userRatedMovies: [],
      allFilms: [],
    };
  },
  
  methods: {
    fetchLatestReleases() {
      
    },
    fetchUserRatedMovies() {
      
    },
    fetchAllFilms() {
      
    },
  },
  mounted() {
    this.fetchLatestReleases();
    this.fetchUserRatedMovies();
    this.fetchAllFilms();
  },
}
</script>