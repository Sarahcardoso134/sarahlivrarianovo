<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      livros: [
        { id: "001", nome: "É assim que Acaba" },
        { id: "002", nome: "O Acordo" },
        { id: "003", nome: "After" },
        { id: "004", nome: "Acotar" },
        { id: "005", nome: "Stranger Things" },
        { id: "006", nome: "Um de nós esta'mendindo" },
        { id: "007", nome: "O Clube do livro dos homens" },
      ],
      novo_livro: "",
    };
  },

  methods: {
    salvar() {
      if (this.novo_livro !== "") {
        const novo_id = uuidv4();
        this.livros.push({
          id: novo_id,
          nome: this.novo_livro,
        });
        this.novo_livro = "";
      }
    },
    excluir(livros) {
      const indice = this.livros.indexOf(livros);
      this.livros.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Livros</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_livro" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-livros">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Título</th>
            <th>ISBN</th>
            <th>Quantidade</th>
            <th>Preço</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.nome }}</td>
            <td>978 – 85 – 333 – 0227 – 3</td>
            <td><button @click="excluir(livro)">Excluir</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
.title {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}
.form-input {
  margin-top: 10px;
  display: flex;
  justify-content: center;
}

.form-input input {
  width: 60%;
  height: 40px;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 0 10px;
}

.form-input button {
  margin-left: 1%;
  width: 20%;
  height: 40px;
  border: 1px solid rgb(0, 0, 0);
  border-radius: 10px;
  background-color: rgb(0, 0, 0);
  color: white;
  font-weight: bold;
  cursor: pointer;
}

.list-editoras {
  display: flex;
  justify-content: center;
}

table {
  width: 50%;
  margin: 2% auto;
  border-collapse: collapse;
}

table tr th {
  border: 1px solid #ccc;
  padding: 10px;
  font-weight: bold;
}

table tr td {
  border: 1px solid #ccc;
  padding: 10px;
}

table tr:nth-child(odd) {
  background-color: #ccc;
}
</style>
