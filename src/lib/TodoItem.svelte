<script lang="ts">
  export let id: number;
  export let title: string;
  export let completed: boolean;
</script>

<div>
  <input type="checkbox" id={id.toString()} bind:checked={completed} />
  <label
    for={id.toString()}
    style="text-decoration: {completed ? 'line-through' : 'none'}"
  >
    {title}
  </label>
</div>
