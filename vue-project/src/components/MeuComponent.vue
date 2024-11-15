<template>
  <div>
    <h1>Gerenciador de Livros</h1>
    
    <input v-model="novoLivro.autor" placeholder="Autor" />
    <input v-model="novoLivro.descricao" placeholder="Nome do livro" />
    <select v-model="novoLivro.categoria">
      <option value="" disabled selected>Categoria</option>
      <option value="Terror">Terror</option>
      <option value="Romance">Romance</option>
      <option value="Ficção">Ficção</option>
    </select>
    
    <button @click="adicionarLivro">Cadastrar Livro</button>
    
    <ul> 
      <li v-if="livros.length === 0">Nenhum livro cadastrado.</li>
      <li v-for="(livro, index) in livros" :key="index">
        {{ livro.autor }} - {{ livro.descricao }} ({{ livro.categoria }})
        <button @click="removerLivro(index)">Deletar</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue' // para atualizar a interface do querido

const novoLivro = ref({ //resgatando as informações que o usuario deve fornecer
  autor: '',
  descricao: '',
  categoria: ''
})

const livros = ref([]) //array inciando vazio

function adicionarLivro() { // funcao para adicionar o livro
  if (novoLivro.value.autor && novoLivro.value.descricao && novoLivro.value.categoria) { //
    livros.value.push({ ...novoLivro.value }) //usando ... para agrantir que toas as info estajam dentro de novoLivro agr
    novoLivro.value = { autor: '', descricao: '', categoria: '' } //limpando os campos
  }
}

function removerLivro(index) { // removendo a partir do index
  livros.value.splice(index, 1)// usando splice para remover os arquivos do array baseando-se no index
}
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  background-color: #f9f9f9;
}

h1 {
  text-align: center;
  color: #fff;
}

input, select {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box; 
}

button {
  background-color: #007bff;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  width: 100%;
  margin: 5px 0;
}

button:hover {
  background-color: #0056b3; 
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

li:last-child {
  border-bottom: none; 
}

li button {
  background-color: #dc3545; 
}

li button:hover {
  background-color: #c82333; 
}
</style>