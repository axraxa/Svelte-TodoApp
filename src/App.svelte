<script>
  let storage = JSON.parse(localStorage.getItem("todos")) || [];
  let input = "";
  function addTodo() {
    if (input) {
      storage = [...storage, input];
      localStorage.setItem("todos", JSON.stringify(storage));
      input = "";
    } else {
      alert("Input your todo.");
    }
  }
  function removeTodo(todo) {
    let filtered = storage.filter((todos) => todos != todo);
    storage = filtered;
    localStorage.setItem("todos", JSON.stringify(filtered));
  }
</script>

<main>
  <h1>TODOS</h1>
  <input
    type="text"
    value={input}
    on:keyup={(e) => (input = e.target?.value)}
    on:submit={(e) => e.preventDefault()}
  />
  <button on:click={addTodo}>Add item</button>
  {#if storage.length > 0}
    <container class="another">
      {#each storage as todo}
        <div class="line">
          <p>{todo}</p>
          <button on:click={() => removeTodo(todo)}>Remove</button>
        </div>
      {/each}
    </container>
  {/if}
</main>

<style>
</style>
