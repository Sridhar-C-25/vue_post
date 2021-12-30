<template>
  <div class="container">
    <ul class="list-group">
      <li
        @dblclick="setremind"
        :class="{ reminder: todo.completed }"
        class="list-group-item mt-2"
      >
        {{ todo.title }}
        <button class="btn btn-danger" @click="$emit('del', todo.id)">
          Delete
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {};
  },

  props: ["todo"],
  methods: {
    setremind() {
      this.$emit("up", this.todo.id);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  font-size: 1.3rem;
  text-transform: capitalize;
  background: rgb(27, 26, 26);
  color: aliceblue;
  animation: list 1s linear forwards;
  transform: scale(0);
}
@keyframes list {
  100% {
    transform: scale(1);
  }
}
.reminder {
  border-left: 15px solid red;
}
button {
  float: right;
  cursor: pointer;
}
</style>
