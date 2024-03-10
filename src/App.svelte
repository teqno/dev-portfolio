<script lang="ts">
  import Window from "./lib/Window.svelte";
</script>

<main>
  <div class="nav">
    <Window
      position={{ x: 20, y: 20 }}
      content={["Egor Filonov", "Software Engineer"]}
    />
    <Window
      position={{ x: 20, y: 300 }}
      title="About"
      content={[
        "Fullstack Developer",
        "Game Programmer",
        "Team player",
        "Performance-oriented",
        "Result-driven",
      ]}
    />
    <Window
      position={{ x: -100, y: 20 }}
      title="Contact"
      content={[
        "filonovyegor@gmail.com",
        { text: "https://github.com/teqno", isURL: true },
        { text: "https://www.linkedin.com/in/egor-filonov-7b4912160", isURL: true },
      ]}
      width={25}
    />
    <Window
      position={{ x: window.innerWidth * 0.25, y: 20 }}
      title="Projects"
      content={[{ text: "https://github.com/teqno/X-Survivors", isURL: true }, { text: "https://github.com/teqno/rust-bevy-game", isURL: true }, { text: "https://github.com/teqno/OpenGL-Rendering-Engine", isURL: true }]}
      width={40}
      height={40}
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

  @media screen and (max-width: 600px) {
    .nav {
      justify-content: flex-start;
    }
  }
</style>
