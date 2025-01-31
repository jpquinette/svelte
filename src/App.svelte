<ValueTest value={'Jp'}/>

<script>

  import ValueTest from './lib/ValueTest.svelte';

  let todos = [
    { text: 'Lait', done: false },

    { text: 'Viande', done: false },
    { text: 'Il était un petit navire', done: false },
    { text: 'Jus', done: false },
    { text: 'Lait', done: false },
    { text: 'Sucre', done: false },
  ];

  let todofield = '';
</script>

<div class="p-4 m-4 rounded-lg">
  

  <div class="flex flex-wrap justify-center gap-4">
    {#each todos as todo, i}
      <button class="item-btn p-4 rounded-lg flex justify-between items-center cursor-pointer 
               bg-gray-200 text-gray-900 dark:bg-gray-800 dark:text-white"
        on:click|preventDefault={() => {
          todos = todos.filter((t) => t !== todo);
        }}
      >
        <p class="text-left font-semibold">{todo.text}</p>
        <p class="text-right m-1">
          X
        </p>
      </button>
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
    class="m-4"
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
