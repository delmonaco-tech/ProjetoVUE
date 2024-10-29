<template>
  <div id="app">
    <h1>Cadastro de Filmes</h1>
    <MovieForm @add-movie="addMovie" />
    <div v-if="movies.length">
      <ul class="movie-list">
        <li v-for="(movie, index) in movies" :key="index" class="movie-item">
          <span>{{ movie.title }} - {{ movie.director }} ({{ movie.year }})</span>
          <button @click="removeMovie(index)" class="delete-button">Deletar</button>
        </li>
      </ul>
    </div>
    <p v-else class="no-movies">Nenhum filme cadastrado.</p>
  </div>
</template>

<script>
import MovieForm from './components/MovieForm.vue';

export default {
  name: 'App',
  components: {
    MovieForm,
  },
  data() {
    return {
      movies: [],
    };
  },
  methods: {
    addMovie(movie) {
      this.movies.push(movie);
    },
    removeMovie(index) {
      this.movies.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
  max-width: 600px;
  margin: 0 auto;
}

h1 {
  color: #333;
  font-size: 2em;
  margin-bottom: 20px;
}

.movie-list {
  list-style-type: none;
  padding: 0;
}

.movie-item {
  background-color: #ffffff;
  margin: 10px 0;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}

.delete-button {
  background-color: #ff4d4d;
  color: #fff;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 3px;
  transition: background-color 0.3s ease;
}

.delete-button:hover {
  background-color: #ff3333;
}

.no-movies {
  color: #777;
  font-size: 1.2em;
  margin-top: 20px;
}
</style>
