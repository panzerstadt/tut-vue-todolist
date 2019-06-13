<script>
export default {
  name: "Todo",
  data() {
    return {
      todos: [],
      input: ""
    };
  },
  methods: {
    add() {
      this.todos.push(this.input);
      this.input = "";
    }
  }
};
</script>

<template>
  <div>
    <div class="row">
      <div class="col-md-12">
        <div class="well">
          <h2>Create a New Todo</h2>
          <form v-on:submit="(e) => {e.preventDefault(); add();}">
            <div class="form-group">
              <label for="todoitem">Todo Item</label>
              <input
                class="form-control"
                type="text"
                v-model="input"
                placeholder="Todo Item"
                name="todo-input"
                id="todoitem"
              >
              <br>
              <button type="button" v-on:click="add()" class="btn btn-default">Create</button>
            </div>
          </form>
        </div>
      </div>

      <div class="col-md-12">
        <h2>List</h2>
        <ul class="list-group">
          <li
            v-for="(todo, index) in todos"
            :key="index"
            class="list-group-item"
          >{{index + 1}} : {{todo}}</li>
        </ul>
      </div>
    </div>

    <div class="row"></div>
  </div>
</template>
