<script>
  export let item;
  import { createEventDispatcher } from "svelte";
  const evt = createEventDispatcher();

  function deleteItem() {
    evt("delete", item.id);
  }

  function completeItem() {
    evt("complete", item.id);
  }
</script>

<div class="card card-body shadow mb-3">
  <div class="row">
    <div class="col-12">
      <div class="card-title">
        <strong class="mr-2">{item.text}</strong>&nbsp;
        {#if item.state}
          <span class="badge rounded-pill bg-success">
            <i class="bi bi-check" />
          </span>
        {:else}
          <span class="badge rounded-pill bg-warning text-dark">
            <i class="bi bi-hourglass-split" />
          </span>
        {/if}
      </div>
    </div>
    <div class="col-12">
      <button class="btn btn-danger btn-sm" on:click={deleteItem}>
        <i class="bi bi-trash" /></button
      >&nbsp;
      <button class="btn btn-success btn-sm" on:click={completeItem}>
        <i class="bi bi-check2-square" />
      </button>
    </div>
  </div>
</div>
