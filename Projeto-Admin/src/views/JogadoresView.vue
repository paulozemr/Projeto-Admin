<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      livro: "",
      editora: "",
      categoria: "",
      preco: "",
      autor:"",
      livros: [
        { id: 1, livro: "Harry Potter", editora: "Bloomsbury Publishing", categoria: "Fantasia", autor: "J.K. Rowling", preco: "25,00" },
        { id: 2, livro: "1984", editora: "Companhia das Letras", categoria: "Ficção", autor: "George Orwell", preco: "29,99" },
      ],
    };
  },
  methods: {
    salvar() {
     if (this.livro !== "") {
      const id = uuid();
      this.livros.push({
        id: id,
        livro: this.livro,
        editora: this.editora,
        categoria: this.categoria,
        autor: this.autor,
        preco: this.preco,
      });
      this.livro = "";
      this.editora = "";
      this.categoria = "";
      this.autor = "";
      this.preco = "";
      } else {
      alert("Informe as coisas!") 
      } 
     },
   excluir(livro) {
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
    },
},
};
</script>
<template>
  <main>
    <div class="container">
      <div class="title">
        <h2>Cadastro De Livros</h2>
      </div>
      <div class="form-input">
        <input type="text" name="" id="" placeholder="Livro" v-model="livro" />
        <input type="text" name="" id="" placeholder="Editora" v-model="editora" />
        <input type="text" name="" id="" placeholder="Autor" v-model="autor" />
        <input type="number" name="" id="" placeholder="Preço" v-model="preco" />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="list-times">
        <table>
          <thead>
            <tr>
              <th>Livro</th>
              <th>Editora</th>
              <th>Categoria</th>
              <th>Autor</th>
              <th>Preço(R$)</th>
              <th>Ações</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="livro in livros" :key="livro.id">
              <th>{{ livro.livro }}</th>
              <th>{{ livro.editora }}</th>
              <th><select>
                  <option>...</option>
                  <option>Ficção</option>
                  <option>Romance</option>
                  <option>Drama</option>
                  <option>Ação</option>
                  <option>Hentão</option>
              </select></th>
              <th>{{ livro.autor}}</th>
              <th>{{ livro.preco }}</th>
              <th><button @click="excluir">Excluir</button></th>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </main>
</template>
<style scoped>
.title {
  text-align: center;
  margin: 2rem 0;
}
.form-input {
  display: flex;
  justify-content: center;
}
.form-input input {
  width: 15%;
  border: 1px solid black;
  border-radius: 10px;
  padding: 0 0.5rem;
  height: 35px;
}
.form-input button {
  height: 40px;
  margin-left: 1%;
  background-color: rgb(71, 11, 103);
  font-weight: bold;
  color: white;
  border-radius: 10px;
  width: 10%;
  transition: 0.25s;
  border: 0px;
}
.list-times {
  display: flex;
  justify-content: center;
  margin: 2rem 0;
}
table {
  width: 50%;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px, rgb(0, 0, 0) 0px 0px 0px 3px;
  border-collapse: collapse;
  text-align: center;
}
table thead {
  background-color: rgb(0, 0, 0);
  color: white;
}
table thead th {
  font-weight: bolder;
}
table tbody tr:nth-child(odd) {
  background-color: rgb(92, 133, 18);
  color: white;
}
</style>
