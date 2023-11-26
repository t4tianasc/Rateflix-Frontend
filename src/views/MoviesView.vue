<template>
  <div class="grid-container">
    <div v-for="movie in allFilms" :key="movie.id" class="grid-item">
      <div>
        <img style="width: 200px;" :src="movie.thumbnail" alt="movie.genre" />
        <div style="display:block; width: 45px;">
          <p class="title-movie">{{ movie.title }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { getAPI } from '../axios-api'

export default {
  name: "MoviesView",
  data() {
    return {
      allFilms: [],
    };
  },
  methods: {
    fetchAllFilms() {
      getAPI.get('/movies/movies',)
        .then(response => {
          this.allFilms = response.data
        })
        .catch(err => {
          console.log(err);
        })
    },
  },
  mounted() {
    this.fetchAllFilms();
  },
};
</script>

<style scoped>
.grid-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.grid-item {
  flex: 0 0 calc(20% - 10px);
  margin: 30px;
  background-color: #ebeaea;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  border-radius: 10px;
}
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