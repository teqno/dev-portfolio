<script lang="ts">
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let isVisible: boolean;
  export let url: string | null = null;
  export let phone: string | null = null;
  export let email: string | null = null;

  function onClick() {
    dispatch("click");
  }
</script>

{#if isVisible}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="fullscreen_overlay" on:click={onClick}>
    {#if url}
      <img src={url} alt="" />
    {/if}
    {#if phone || email}
      <div
        class="text_container"
        on:click={(event) => {
          event.stopPropagation();
        }}
      >
        <p>{phone}</p>
        <p>{email}</p>
      </div>
    {/if}
  </div>
{/if}

<style>
  .fullscreen_overlay {
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }

  img {
    max-width: 80vw;
  }

  .text_container {
    border-radius: 4px;
    background-color: sienna;
    min-width: 200px;
    min-height: 100px;
    padding: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
</style>
