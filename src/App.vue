<template>
  <div>
    <h1>Todo List</h1>
    <div>
      <input type="text" v-model="newTodo" placeholder="Tambahkan todo">
      <button @click="addTodo">Tambah</button>
    </div>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">{{ todo }}</li>
    </ul>
    <p v-if="isHebat">Hebat!</p>
    <button class="reset-button" @click="resetTodos">Reset</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  computed: {
    isHebat() {
      return this.todos.length >= 4;
    },
    isTodoEmpty() {
      return this.newTodo.trim() === '';
    }
  },
  methods: {
    addTodo() {
      if (!this.isTodoEmpty) {
        this.todos.push(this.newTodo.trim());
        this.newTodo = '';
      }else{
        alert('Tidak Boleh kosong');
      }
    },
    resetTodos() {
      this.todos = [];
    }
  },
  watch: {
    todos: {
      handler(newTodos) {
        console.log('Todos changed:', newTodos);
      },
      deep: true
    }
  }
};
</script>

<style scoped>
ul {
  list-style-type: decimal;
  margin-left: 20px;
  margin-top: 10px;
}

li {
  margin-bottom: 8px;
}

p {
  margin-top: 10px;
  color: green;
}

.reset-button {
  background-color: #dc3545;
  margin-top: 20px;
}
</style>
