<template>
  <carousel :items-to-show="7">
    <slide v-for="movie in allFilms" :key="movie.id">
      <div style="">
        <div>
          <img style="width: 200px;" :src="movie.thumbnail" alt="movie.genre" />
          <div style="display:block; width: 45px;">
            <p class="title-movie">{{ movie.title }}</p>
          </div>
        </div>
      </div>
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
      latestReleases: [],
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

<style scoped>
.title-movie {
  text-overflow: ellipsis;
  width: 200px;
  height: 45px;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
</style>