<ValueTest value={'Jp'}/>

<script>

  import ValueTest from './lib/ValueTest.svelte';

  let todos = [
    { text: 'Lait', done: true },

    { text: 'Viande', done: false },
  ];

  let todofield = '';
</script>

<div class="p-4 m-4 bg-gray-200 rounded-lg">
  
  <!-- GRID avec max 4 colonnes -->
  <div class="grid grid-cols-4 gap-4">
    {#each todos as todo, i}
      <div class="bg-white p-4 rounded-lg shadow-md flex justify-between items-center cursor-pointer"
        on:click|preventDefault={() => {
            todos = todos.filter((t) => t !== todo);
          }}
      >
        <p class="text-center font-semibold">{todo.text}</p>
        <button
          
          class="m-0 p-0"
        >
          X
        </button>
      </div>
    {/each}
  </div>

  <!-- Formulaire d'ajout -->
  <form
    on:submit|preventDefault={() => {
      if (todofield.trim() !== '') {
        todos = [...todos, { text: todofield, done: false }];
        todofield = '';
      }
    }}
    class="mt-4 flex justify-center gap-2"
  >
    <input
      type="text"
      name="todo"
      id="todo"
      class="rounded-md p-3 text-sm border border-gray-400"
      bind:value={todofield}
      placeholder="Ajouter un item"
    />
    <button class="bg-blue-500 text-white px-4 py-2 rounded-md hover:bg-blue-600">+</button>
  </form>

</div>
