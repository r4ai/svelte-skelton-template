<script lang="ts">
  export let id: number;
  export let title: string;
</script>

<div>
  <input type="checkbox" id={id.toString()} />
  <label for={id.toString()}>{title}</label>
</div>
