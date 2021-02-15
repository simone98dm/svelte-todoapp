<script>
  import Item from "./Item.svelte";
  export let items;
</script>

<div>
  {#each items as item}
    <Item {item} on:complete on:delete />
  {/each}
</div>

<style></style>
