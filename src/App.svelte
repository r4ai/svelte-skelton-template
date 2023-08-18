<script lang="ts">
  import TodoItem from "./lib/TodoItem.svelte";

  type Todo = {
    id: number;
    title: string;
    completed: boolean;
  };

  let todos: Todo[] = localStorage.getItem("todos")
    ? JSON.parse(localStorage.getItem("todos"))
    : [];

  console.log("rendered");

  $: localStorage.setItem("todos", JSON.stringify(todos));

  let todoTitle = "";

  const handleAddTodo = () => {
    todos = [
      ...todos,
      { id: todos.length + 1, title: todoTitle, completed: false },
    ];
    todoTitle = "";
  };

  const deleteTodo = (id: number) => {
    todos = todos.filter((x) => x.id !== id);
  };
</script>

<main>
  <h2>ToDo List</h2>
  <div>
    <h3>未完了</h3>
    {#each todos.filter((x) => !x.completed) as todo}
      <TodoItem
        id={todo.id}
        title={todo.title}
        bind:completed={todo.completed}
        {deleteTodo}
      />
    {/each}
  </div>
  <div>
    <h3>完了済み</h3>
    {#each todos.filter((x) => x.completed) as todo}
      <TodoItem
        id={todo.id}
        title={todo.title}
        bind:completed={todo.completed}
        {deleteTodo}
      />
    {/each}
  </div>
  <form on:submit|preventDefault={handleAddTodo}>
    <input type="text" placeholder="Add a new ToDo" bind:value={todoTitle} />
    <button>Add</button>
  </form>
</main>

<style>
  form {
    margin-top: 1rem;
  }
</style>
