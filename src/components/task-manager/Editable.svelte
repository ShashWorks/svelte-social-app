<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let value;
  let isEditing = false;
</script>

{#if isEditing}
  <div class="flex-it">
    <!-- <textarea bind:value={value} /> -->
    <textarea bind:value />
    <button
      on:click={() => {
        isEditing = false;
        dispatch("editClose", {
          taskText: value
        });
        //basically we can pass anything by creating an object
        // dispatch("editClose", {
        //   taskText: "Hi There!",
        //   someNUm: 100 
        // });
      }}
      class="flex underline">Close</button
    >
  </div>
{:else}
  <button
    on:click={() => {
      isEditing = true;
    }}
  >
    <slot />
  </button>
{/if}
