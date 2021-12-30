<template>
  <div class="container">
    <br />
    <input
      type="button"
      class="btn btn-primary"
      @click="formShow = !formShow"
      :value="formShow ? 'Add Todo +' : 'x Close'"
    /><br /><br />
    <form class="form" :class="{ showForm: formShow }">
      <div class="form-group">
        <label for="text" class="form-label"> Enter the Task : </label>
        <div class="d-flex">
          <input type="text" class="form-control" v-model="txt" />
          <button class="btn btn-success" @click.prevent="Add()">
            Add Todo
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      txt: "",
      formShow: true,
    };
  },
  methods: {
    Add() {
      if (this.txt !== "") {
        const newTodo = {
          id: Math.random() * 10000,
          title: this.txt,
          complete: false,
        };
        this.$emit("cre", newTodo);
        this.txt = "";
      } else {
        alert("Please Enter the todo!!!");
      }
    },
  },
};
</script>

<style>
input {
  border-radius: 0 !important;
  opacity: 0;
  animation: list 2s linear forwards;
}
@keyframes list {
  100% {
    opacity: 1;
  }
}

button {
  font-family: inherit;
  flex: 30%;
  border-radius: 0 !important;
}
.btn-primary {
  float: right;
}
.btn-success {
  animation: list 2s linear forwards;
  opacity: 0;
}
.form {
  padding: 40px 0;
}
.form-label {
  font-size: 1.4rem;
  font-weight: bold;
  text-transform: uppercase;
}
.showForm {
  display: none;
}
</style>