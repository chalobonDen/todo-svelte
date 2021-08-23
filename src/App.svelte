<script>
  let newItem = '';

  let todoList = [
    { text: 'Write my first post', status: true },
    { text: 'Upload the post to the blog', status: false },
    { text: 'Publish the post at Facebook', status: false },
  ];

  function addToList() {
    if (newItem.trim().length > 0) {
      todoList = [...todoList, { text: newItem, status: false }];
      newItem = '';
    } else {
      alert(`can't add this todo`);
      newItem = '';
    }
  }

  function removeFromList(index) {
    todoList.splice(index, 1);
    todoList = todoList;
  }
</script>

<main>
  <h1>Todo List</h1>
  <input bind:value={newItem} type="text" placeholder="new todo item.." />
  <button on:click={addToList}>Add</button>

  <ul>
    {#each todoList as item, index}
      <input bind:checked={item.status} type="checkbox" />
      <span class:checked={item.status}>{item.text}</span>
      <span on:click={() => removeFromList(index)}>❌</span>
      <br />
    {/each}
  </ul>
</main>

<style>
  .checked {
    text-decoration: line-through;
  }

  h1 {
    color: #717eb8;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  .active {
    text-decoration: line-through;
  }

  main {
    text-align: center;
    font-family: sans-serif;
  }

  li {
    list-style-type: none;
  }
</style>
