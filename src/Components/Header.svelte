<script>
  export let count;
</script>

<div class="m-2">
  {#if count > 0}
    <h3>You have {count} left</h3>
  {:else}
    <h3>You have completed all your todo!</h3>
  {/if}
</div>
