<script lang="ts">
  import TodoItem from "./lib/TodoItem.svelte";
</script>

<main>
  <h2>ToDo List</h2>
  <div>
    <TodoItem id={1} title="Test1" />
    <TodoItem id={2} title="Test2" />
  </div>
  <form>
    <input type="text" placeholder="Add a new ToDo" />
    <button>Add</button>
  </form>
</main>

<style>
  form {
    margin-top: 1rem;
  }
</style>
