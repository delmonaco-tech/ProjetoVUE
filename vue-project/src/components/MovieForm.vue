<template>
  <div class="movie-form">
    <input
      type="text"
      v-model="title"
      placeholder="Título do Filme"
      required
    />
    <input
      type="text"
      v-model="director"
      placeholder="Diretor"
      required
    />
    <input
      type="number"
      v-model="year"
      placeholder="Ano de Lançamento"
      required
    />
    <button @click="handleSubmit" class="submit-button">Cadastrar Filme</button>
  </div>
</template>

<script>
export default {
  name: 'MovieForm',
  data() {
    return {
      title: '',
      director: '',
      year: '',
    };
  },
  methods: {
    handleSubmit() {
      if (this.title && this.director && this.year) {
        const newMovie = {
          title: this.title,
          director: this.director,
          year: this.year,
        };
        this.$emit('add-movie', newMovie);
        this.clearForm();
      } else {
        alert("Todos os campos são obrigatórios!");
      }
    },
    clearForm() {
      this.title = '';
      this.director = '';
      this.year = '';
    },
  },
};
</script>

<style scoped>
.movie-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

input {
  width: 80%;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 1em;
}

.submit-button {
  width: 85%;
  padding: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1em;
  transition: background-color 0.3s ease;
}

.submit-button:hover {
  background-color: #45a049;
}
</style>
