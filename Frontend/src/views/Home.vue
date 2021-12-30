<template>
  <div class="home">
    <AddTodo @cre="cre" />
    <div v-for="todo in todos" :key="todo.id">
      <HelloWorld :todo="todo" @del="del(todo.id)" @up="up(todo.id)" />
    </div>
  </div>
</template>

<script>
import HelloWorld from "../components/HelloWorld.vue";
import AddTodo from "../components/AddTodo.vue";
// @ is an alias to /src
export default {
  name: "Home",
  components: {
    HelloWorld,
    AddTodo,
  },
  methods: {
    async del(id) {
      if (confirm("are you sure?")) {
        console.log(id);
        await fetch(`http://localhost:3000/todos/${id}`, {
          method: "DELETE",
        });

        this.todos = this.todos.filter((todo) => todo.id !== id);
      }
    },
    async cre(title) {
      const res = await fetch("http://localhost:3000/todos", {
        method: "POST",
        body: JSON.stringify({
          id: title.id,
          title: title.title,
          completed: title.complete,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      });

      const data = await res.json();

      this.todos = [...this.todos, data];
    },
    async up(id) {
      // console.log(id);
      // const toggle = await this.fetchData(id);
      // const upd = { ...toggle, completed: !toggle.completed };
      // console.log(toggle.id);

      this.todos = this.todos.map((todo) =>
        todo.id === id ? { ...todo, completed: todo.completed } : todo
      );
    },

    async fetchData() {
      const res = await fetch("http://localhost:3000/todos");

      const data = await res.json();
      return data;
    },
  },
  data() {
    return {
      todos: [],
    };
  },
  async created() {
    this.todos = await this.fetchData();
  },
  props: ["todo"],
};
</script>

<style scoped>
.home {
  /* min-width:45%; */
  margin: auto;
}
</style>
