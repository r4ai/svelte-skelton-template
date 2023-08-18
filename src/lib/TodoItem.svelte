<script lang="ts">
  export let id: number;
  export let title: string;
  export let completed: boolean;
  export let deleteTodo: (id: number) => void;
</script>

<div>
  <input type="checkbox" id={id.toString()} bind:checked={completed} />
  <label
    for={id.toString()}
    style="text-decoration: {completed ? 'line-through' : 'none'}"
  >
    {title}
  </label>
  <button on:click={() => deleteTodo(id)}>×</button>
</div>
