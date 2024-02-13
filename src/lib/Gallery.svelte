<script lang="ts">
  import FullscreenOverlay from "./FullscreenOverlay.svelte";
  import GalleryItem from "./GalleryItem.svelte";

  export let images: string[];

  let isImageOverlayVisible = false;
  let currentGalleryItemUrl: string;

  const handleGalleryItemClick = (event: CustomEvent<{ url: string }>) => {
    isImageOverlayVisible = true;
    currentGalleryItemUrl = event.detail.url;
  };

  const hideOverlay = () => {
    isImageOverlayVisible = false;
  };
</script>

<div class="gallery">
  {#each images as image}
    <GalleryItem url={image} on:click={handleGalleryItemClick} />
  {/each}
</div>
<FullscreenOverlay
  isVisible={isImageOverlayVisible}
  url={currentGalleryItemUrl}
  on:click={hideOverlay}
/>

<style>
  .gallery {
    visibility: hidden;
    margin: 16px;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    gap: 8px;
  }
</style>
