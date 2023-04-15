<script>
  import { createEventDispatcher } from "svelte";

  export let items;
  export let activeItem;
  const dispatch = createEventDispatcher();
</script>

<div class="tabs">
  <ul>
    {#each items as item}
      <li on:click={() => dispatch('tabChange', item)}>
        <div class:active={item === activeItem}>{item}</div>
      </li>
    {/each}
  </ul>
</div>

<style>
  .tabs {
    margin-bottom: 40px;
  }
  ul {
    display: flex;
    justify-content: center;
    list-style-type: none;
    padding: 0;
    padding-top: 20px;
  }
  li {
    color: #555;
    margin: 0px 16px;
    font-size: 18px;
    cursor: pointer;
  }
  .active {
    color: #d91b42;
    border-bottom: 2px solid #d91b42;
    padding-bottom: 8px;
  }
</style>
