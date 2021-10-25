<template>
  <div class="row justify-content-md-center">
    <Header />
    <div class="col-sm-8 mb-5">
      <table class="table mt-5">
        <thead class="thead-dark">
          <tr>
            <th><h1>Todo App</h1></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(todo, index) in todoList" :key="index">
            <td class="align-middle w-75">
              {{ todo.content }}
            </td>
            <td class="align-middle text-center w-75">
               <span data-toggle="tooltip" data-placement="left" title="éditer">
              <button class="btn btn-dark btn-sm mx-1" @click="Edit(todo.id)">
                <i class="fas fa-pencil-alt"></i>
              </button>
               </span>
               <span data-toggle="tooltip" data-placement="right" title="Supprimer">
              <button
                class="btn btn-danger btn-sm mx-1"
                @click="Delete(todo.id)"
              >
                <i class="far fa-trash-alt"></i>
              </button>
               </span>
            </td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td class="align-middle ">
              <div class="form-group">
                <h4>{{ editMode ? "Éditer" : "Ajouter" }}</h4>

                <input
                  type="text"
                  class="form-control"
                  v-model="todoItem.content"
                  @keyup.enter="TodoItem"
                />
              </div>
            </td>
            <td class="align-middle text-center w-75">
              <button class="btn btn-dark btn-sm mx-1" @click="TodoItem">
                {{ editMode ? "Éditer" : "Ajouter" }}
              </button>
              <button
                v-if="editMode"
                class="btn btn-danger btn-sm mx-1"
                @click="Cancel"
              >
                Annuler
              </button>
            </td>
          </tr>
        </tfoot>
      </table>
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Axios from "axios";
const todoUrl = "http://localhost:3500/todos";

export default {
  data() {
    return {
      todoList: {},
      todoItem: {},
      editMode: false,
    };
  },
  components: {
    Header,
    Footer,
  },
  methods: {
    Edit(id) {
      this.editMode = true;
      this.todoItem = this.todoList.find((todo) => todo.id == id);
    },
    Cancel() {
      this.editMode = false;
      this.todoItem = "";
    },

    async TodoItem() {
      const id = this.todoItem.id;

      if (this.editMode) {
        await Axios.put(`${todoUrl}/${id}`, this.todoItem);
        this.editMode = false;
        this.todoItem.content = "";
      } else {
        await Axios.post(todoUrl, this.todoItem);

        this.todoItem.content = "";
      }

      Axios.get(todoUrl).then((res) => (this.todoList = res.data));
    },
    async Delete(id) {
      await Axios.delete(`${todoUrl}/${id}`);
      Axios.get(todoUrl).then((res) => (this.todoList = res.data));
    },
  },
  created() {
    // avoir la liste des todos
    Axios.get(todoUrl).then((res) => (this.todoList = res.data));
  },
};
</script>

<style>
.bs-tooltip-top {
  margin-bottom: 10px !important;
}

.bs-tooltip-right {
  margin-left: 10px !important;
}
.bs-tooltip-bottom {
  margin-top: 10px !important;
}

.bs-tooltip-left {
  margin-right: 10px !important;
}
</style>
