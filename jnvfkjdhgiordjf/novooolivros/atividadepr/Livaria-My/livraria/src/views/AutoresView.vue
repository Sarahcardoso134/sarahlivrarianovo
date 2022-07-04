<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      autores: [
        { id: "001", nome:"Collen Hoover" },
        { id: "002", nome: "Elle Kennedy" },
        { id: "003", nome: "Anna Told" },
        { id: "004", nome: "Sarah J. Maas" },
        { id: "005", nome: "Gwenda Bond" },
        { id: "006", nome: "Karen Mcmanus" },
        { id: "007", nome: "Lissa Kay Adams" },
      ],
      novo_autor: "",
    };
  },

  methods: {
    salvar() {
      if (this.novo_autor !== "") {
        const novo_id = uuidv4();
        this.autores.push({
          id: novo_id,
          nome: this.novo_autor,
        });
        this.novo_autor = "";
      }
    },
    excluir(autores) {
      const indice = this.autores.indexOf(autores);
      this.autores.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Autores</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_autor" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-autores">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="autores in autores" :key="autores.id">
            <td>{{ autores.id }}</td>
            <td>{{ autores.nome }}</td>
            <td>
              <button @click="excluir(autores)">Excluir</button>
            </td>
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
  border: 1px solid rgb(36, 127, 65);
  border-radius: 10px;
  background-color: rgb(36, 127, 65);
  color: white;
  font-weight: bold;
  cursor: pointer;
}

.list-autores {
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
  background-color: black;
}
</style>
