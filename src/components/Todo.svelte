<script>
  import TodoItem from "./TodoItem.svelte";
  let todos = [{ text: "I am for testing", checked: false }];
  let todo = "";

  $: amount = todos.reduce((sum, todo) => (todo.done ? ++sum : sum), 0);
  function addTodo() {
    // if (todo === "") return alert("please input a todo");
    const newTodo = {
      text: todo,
      done: false
    };
    todos = [...todos, { text: "I am for testing", checked: false }];
    todo = "";
  }
</script>

<style>
  .wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .container {
    display: grid;
    grid-template-rows: 8fr 1fr 1fr;
    padding: 8px;
    width: 600px;
    max-width: 800px;
    height: 600px;
    background: aliceblue;
    border: 3px solid #F2BB4D;
    border-radius: 5px;
  }
  .no-todos {
    width: 100%;
    height: 40px;
    font-size: 22px;
  }
  .todos {
    height: 100%;
    overflow-y: auto;
    margin-bottom: 24px;
  }
</style>

<div class="wrapper">
  <div class="container">
    <div class="todos">
      {#each todos as todo}
        <TodoItem bind:todo />
      {:else}
        <p class="no-todos">No todos )))):</p>
      {/each}
    </div>
    <div />
    <button on:click={addTodo}>add todo</button>
    <input bind:value={todo} placeholder="Your Todo Here" />
    <p>You've done {amount} todos out of {todos.length}</p>
  </div>
</div>
