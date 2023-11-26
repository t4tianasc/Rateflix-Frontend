<template>
  <p class="title-section">
    Latest releases
  </p>
  <div class="line-separator"></div>

  <carousel :autoplay="2000" :transition="500" :items-to-show="7">
    <slide v-for="movie in latestReleases" :key="movie.id">
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
import { getAPI } from '../axios-api'

export default {
  name: 'HomeView',
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
      latestReleases: [],
    };
  },
  methods: {
    fetchLatestReleases() {
      getAPI.get('/movies/latest_releases',)
        .then(response => {
          this.latestReleases = response.data
        })
        .catch(err => {
          console.log(err);
        })
    },
  },
  mounted() {
    this.fetchLatestReleases();
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
.title-section {
  font-size: 30px;
  text-align-last: left;
  padding-left: 20px;
}
body {
  font-family: 'Bebas Neue', sans-serif;
}
.line-separator {
  width: 100%;
  height: 1px;
  background-color: #ccc;
  margin: 10px 0;
}
</style>