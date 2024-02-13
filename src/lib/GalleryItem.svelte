<script lang="ts">
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let url: string;

  function onClick() {
    dispatch("click", {
      url,
    });
  }
</script>

<button on:click={onClick} class="gallery_item">
  <img src={url} alt="" />
</button>

<style>
  .gallery_item img {
    width: 10vw;
  }

  .gallery_item {
    padding: 0;
    min-height: 15vw;
    display: flex;
    align-items: center;
  }

  @media screen and (max-width: 1000px) {
    .gallery_item img {
      width: 20vw;
    }

    .gallery_item {
      min-height: 30vw;
    }
  }

  @media screen and (max-width: 600px) {
    .gallery_item img {
      width: 30vw;
    }

    .gallery_item {
      min-height: 45vw;
    }
  }
</style>
