<script>
  export let todo;
  $: console.log(todo);
</script>

<style>
  .container {
    padding: 12px 24px;
    border-bottom: 1px solid silver;
  }
  label {
    display: block;
    padding-left: 15px;
    text-indent: -15px;
  }
  input {
    width: 13px;
    height: 13px;
    padding: 0;
    margin: 0;
    vertical-align: bottom;
    position: relative;
    top: -1px;
  }
  label.done {
      text-decoration: line-through;
  }
</style>

<div class="container">
  <label class:done={todo.done}>
    <input type="checkbox" bind:checked={todo.done} />
    {todo.text}
  </label>
</div>
