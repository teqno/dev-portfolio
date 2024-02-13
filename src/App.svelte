<script lang="ts">
  import FullscreenOverlay from "./lib/FullscreenOverlay.svelte";
  import Gallery from "./lib/Gallery.svelte";
  import Window from "./lib/Window.svelte";

  const images = [
    "_DSC6277.jpg",
    "_DSC6282.jpg",
    "_DSC6283.jpg",
    "_DSC6286.jpg",
    "_DSC6295.jpg",
    "_DSC6296.jpg",
    "_DSC6299.jpg",
    "_DSC6301.jpg",
    "_DSC6322.jpg",
    "_DSC6323.jpg",
    "_DSC6326.jpg",
    "_DSC6330.jpg",
    "_DSC6331.jpg",
    "_DSC6334.jpg",
    "_DSC6335.jpg",
    "_DSC6339.jpg",
    "_DSC6342.jpg",
    "_DSC6344.jpg",
    "_DSC6348.jpg",
    "_DSC6349.jpg",
    "_DSC6352.jpg",
    "_DSC6354.jpg",
    "_DSC6414.jpg",
    "_DSC6415.jpg",
    "_DSC6416-Edit.jpg",
    "_DSC6417-Edit.jpg",
    "_DSC6418-Edit.jpg",
    "_DSC6422.jpg",
    "_DSC6427.jpg",
    "_DSC6429.jpg",
    "_DSC6437.jpg",
    "_DSC6443.jpg",
    "_DSC6449.jpg",
    "_DSC6455.jpg",
    "_DSC6457.jpg",
    "_DSC6463.jpg",
    "_DSC6467.jpg",
    "_DSC6477.jpg",
    "_DSC6482.jpg",
    "_DSC6483.jpg",
    "_DSC6556.jpg",
    "_DSC6559.jpg",
    "_DSC6564.jpg",
    "_DSC6568.jpg",
    "_DSC6574.jpg",
    "_DSC6577.jpg",
    "_DSC6578.jpg",
    "_DSC6578-Enhanced-NR.jpg",
    "_DSC6578-Enhanced-NR-Edit.jpg",
    "_DSC6581.jpg",
    "_DSC6582.jpg",
    "_DSC6589.jpg",
    "_DSC6591.jpg",
    "_DSC6592.jpg",
    "_DSC6593.jpg",
    "_DSC6597.jpg",
    "_DSC6598.jpg",
    "_DSC6599.jpg",
    "_DSC6600.jpg",
    "_DSC6604.jpg",
    "_DSC6641.jpg",
    "_DSC6644.jpg",
    "_DSC6646.jpg",
    "_DSC6648.jpg",
    "_DSC6650.jpg",
    "_DSC6653.jpg",
    "_DSC6660.jpg",
    "_DSC6662.jpg",
    "_DSC6663.jpg",
    "_DSC6665.jpg",
    "_DSC6672.jpg",
    "_DSC6688.jpg",
    "_DSC6689.jpg",
    "_DSC6691.jpg",
    "_DSC6692.jpg",
    "_DSC6693.jpg",
    "_DSC6695.jpg",
    "_DSC6696.jpg",
    "_DSC6698.jpg",
    "_DSC6699.jpg",
    "_DSC6700.jpg",
    "_DSC6705.jpg",
    "_DSC6706.jpg",
    "_DSC6708.jpg",
    "_DSC6709.jpg",
    "_DSC6710.jpg",
    "_DSC6711.jpg",
    "_DSC6713.jpg",
    "_DSC6715.jpg",
    "_DSC6717.jpg",
    "_DSC6719.jpg",
    "_DSC6752.jpg",
    "_DSC6775-Enhanced-NR.jpg",
    "_DSC6779-Enhanced-NR.jpg",
    "_DSC6780.jpg",
    "_DSC6781.jpg",
    "_DSC6782.jpg",
    "_DSC6783.jpg",
    "_DSC6785.jpg",
    "_DSC6788-Enhanced-NR.jpg",
    "_DSC6789-Enhanced-NR.jpg",
    "_DSC6791.jpg",
    "_DSC6793.jpg",
    "_DSC6794-Enhanced-NR.jpg",
    "_DSC6796-Enhanced-NR.jpg",
    "_DSC6805-Enhanced-NR.jpg",
    "_DSC6806-Enhanced-NR.jpg",
    "_DSC6835.jpg",
    "_DSC6836.jpg",
    "_DSC6837.jpg",
    "_DSC6838.jpg",
    "_DSC6839.jpg",
    "_DSC6848.jpg",
    "_DSC6858.jpg",
    "_DSC6860.jpg",
    "_DSC6863.jpg",
    "_DSC6875.jpg",
    "_DSC6876.jpg",
    "_DSC6877.jpg",
    "_DSC6878.jpg",
    "_DSC6882.jpg",
    "_DSC6883.jpg",
    "_DSC6884.jpg",
    "_DSC6885.jpg",
    "_DSC6887.jpg",
    "_DSC6891.jpg",
    "_DSC6892.jpg",
    "_DSC6903.jpg",
    "_DSC6907.jpg",
    "_DSC6914.jpg",
    "_DSC6918.jpg",
    "_DSC6927.jpg",
    "_DSC6933.jpg",
    "_DSC6934.jpg",
    "_DSC6941.jpg",
    "_DSC6944.jpg",
  ].reverse();

  let isContactMeOverlayVisible = false;

  const hideOverlay = () => {
    isContactMeOverlayVisible = false;
  };

  const handleContactMeClick = () => {
    isContactMeOverlayVisible = true;
  };
</script>

<main>
  <div class="nav">
    <Window
      position={{ x: 20, y: 20 }}
      content={["Egor Filonov", "Software Engineer"]}
    />
    <Window
      position={{ x: 20, y: 300 }}
      content={["About Me:", "Good programer"]}
    />
    <Window
      position={{ x: -100, y: 20 }}
      content={["Contact me:", "test@mail.com"]}
    />
    <Window
      position={{ x: 700, y: 20 }}
      content={["Projects:", "Proj 1", "Proj 1", "Proj 1"]}
      width={40}
      height={40}
    />
    <div class="contacts">
      <button on:click={handleContactMeClick}>contact me</button>
    </div>
  </div>
  <div class="content">
    <FullscreenOverlay
      isVisible={isContactMeOverlayVisible}
      phone="0405153451"
      email="filonovyegor@gmail.com"
      on:click={hideOverlay}
    />
  </div>
</main>

<style>
  .nav {
    display: flex;
    justify-content: left;
    align-items: center;
    padding: 16px 32px 0 32px;
    flex: 1 100%;
  }

  .contacts {
    position: absolute;
    top: 0;
    right: 0;
    display: flex;
    flex-wrap: wrap;
    align-items: end;
    justify-content: center;
    flex-direction: column;
    margin: 16px;
    font-family: Teko-Light;
    font-size: 22pt;
  }

  .contacts > * {
    width: fit-content;
    background: none;
    text-transform: uppercase;
  }

  @media screen and (max-width: 600px) {
    .nav {
      justify-content: flex-start;
    }
  }
</style>
