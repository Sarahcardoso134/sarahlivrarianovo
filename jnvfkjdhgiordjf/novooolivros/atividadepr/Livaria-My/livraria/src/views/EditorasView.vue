<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      editoras: [
        { id: "001", nome: "Editora 1" },
        { id: "002", nome: "Editora 2" },
        { id: "003", nome: "Editora 3" },
        { id: "004", nome: "Editora 4" },
        { id: "005", nome: "Editora 5" },
         { id: "006", nome: "Editora 6" },
          { id: "007", nome: "Editora 7" },
      ],
      nova_editora: "",
    };
  },

  methods: {
    salvar() {
      if (this.nova_editora !== "") {
        const novo_id = uuidv4();
        this.editoras.push({
          id: novo_id,
          nome: this.nova_editora,
        });
        this.nova_editora = "";
      }
    },
    excluir(editoras) {
      const indice = this.editoras.indexOf(editoras);
      this.editoras.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Editoras</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="nova_editora" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-editoras">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Site</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="editoras in editoras" :key="editoras.id">
            <td>{{ editoras.id }}</td>
            <td>{{ editoras.nome }}</td>
            <td>www.</td>
            <td><button @click="excluir(editoras)">Excluir</button></td>
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
    background-color: aliceblue;
}
</style>
