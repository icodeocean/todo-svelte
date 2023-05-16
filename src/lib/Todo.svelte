<script lang="ts">
  import { createEventDispatcher } from 'svelte'
  import { fade } from 'svelte/transition'

  import { type TodoType } from '../types'
  const dispatch = createEventDispatcher()

  export let todo: TodoType
</script>

<li transition:fade>
  <input
    type="checkbox"
    checked={todo.done}
    on:change={() => dispatch('toggleDone')}
  />
  <span class:done={todo.done}>{todo.text}</span>
  <button on:click={() => dispatch('delete')}>Delete</button>
</li>

<style>
  .done {
    color: gray;
    text-decoration: line-through;
  }

  li {
    margin-top: 0.5rem;
  }
</style>
