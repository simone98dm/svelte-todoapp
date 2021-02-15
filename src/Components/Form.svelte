<script>
  let todoValue = "";
  import { createEventDispatcher } from "svelte";

  const evt = createEventDispatcher();

  function onSubmitHandler(e) {
    e.preventDefault();
    if(todoValue === "") return;
    const obj = {
      text: todoValue,
      state: false,
    };
    evt("newitem", obj);
  }
</script>

<div class="m-4">
  <form on:submit={onSubmitHandler}>
    <h4>Add new todo</h4>
    <input class="form-control mb-3" maxLength="100" bind:value={todoValue} />
    <button type="submit" class="btn btn-primary btn-sm"
      ><i class="bi bi-plus-circle" />&nbsp;Add</button
    >
  </form>
</div>
