<script lang="ts">
  import { onMount } from "svelte";

  export let title: string = "";
  export let content: (string | { text: string, isURL: boolean })[];
  export let position: { x: number; y: number };
  export let width: number = 20;
  export let height: number = 20;

  let isTextSelectable = "text";
  let isDrag = false;

  onMount(() => {
    position = {
      x:
        position.x > 0
          ? position.x
          : window.innerWidth + position.x - (window.innerWidth * width) / 100,
      y:
        position.y > 0
          ? position.y
          : window.innerHeight +
            position.y -
            (window.innerHeight * height) / 100,
    };
    const parents = document.getElementsByClassName("windowContent");

    for (const parent of parents) {
      const children = parent.children;
      for (let i = 0; i < children.length; i++) {
        const el = children[i];
        (el as HTMLElement).style["animationDelay"] = `${i}s`;
        console.log(el);
      }
    }
  });

  function cssVariables(
    node: HTMLElement,
    variables: { [key: string]: number | string },
  ) {
    setCssVariables(node, variables);

    return {
      update(variables: { [key: string]: number | string }) {
        setCssVariables(node, variables);
      },
    };
  }

  function setCssVariables(
    node: HTMLElement,
    variables: { [key: string]: number | string },
  ) {
    for (const name in variables) {
      console.log(name, variables[name]);

      node.style.setProperty(`--${name}`, `${variables[name]}`);
    }
  }

  const dragStart = () => {
    isDrag = true;
    isTextSelectable = "none";
  };

  const dragMove = (event: MouseEvent) => {
    if (isDrag) {
      position = {
        x: (position.x += event.movementX),
        y: (position.y += event.movementY),
      };
    }
  };

  const dragEnd = () => {
    isDrag = false;
    isTextSelectable = "text";
  };
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div
  class="window"
  use:cssVariables={{
    left: position.x,
    top: position.y,
    width,
    height,
    isTextSelectable,
  }}
>
  <div class="windowHeader" on:mousedown={dragStart}>
    <div class="windowHeaderTitle">
      <h3>{title}</h3>
    </div>
    <div class="icons">
      <svg
        class="svgIcon"
        height="20"
        width="20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <circle r="10" cx="10" cy="10" fill="red" />
      </svg>
      <svg
        class="svgIcon"
        height="20"
        width="20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <circle r="10" cx="10" cy="10" fill="yellow" />
      </svg>
      <svg
        class="svgIcon"
        height="20"
        width="20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <circle r="10" cx="10" cy="10" fill="green" />
      </svg>
    </div>
  </div>
  <div class="windowContent">
    {#each content as item}
      {#if typeof item == 'string' || !item.isURL}
        <p>{item}</p>
      {:else}
        <p><a href={item.text} target="_blank">{item.text}</a></p>
      {/if}
      
    {/each}

  </div>
</div>
<svelte:window on:mouseup={dragEnd} on:mousemove={dragMove} />

<style>
  .window {
    position: absolute;
    left: calc(var(--left) * 1px);
    top: calc(var(--top) * 1px);
    display: flex;
    flex-direction: column;
    width: calc(var(--width) * 1vw);
    height: calc(var(--height) * 1vh);
    background-color: rgba(10, 10, 10, 0.5);
    border: 1px solid rgb(20, 20, 20);
    box-shadow: 5px 5px 5px 0px rgba(0, 0, 0, 0.5);
  }

  .windowHeader {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 40px;
    background-color: rgba(20, 20, 20, 0.5);
  }

  .windowHeaderTitle {
    margin-left: 10px;
  }

  .icons {
    margin-right: 10px;
  }

  .windowContent {
    text-align: left;
    padding: 5px;
    user-select: var(--isTextSelectable);
  }

  .windowContent > * {
    max-width: min-content;
    margin: 0 !important;
  }

  .windowContent * {
    width: 0;
    overflow: hidden; /* Ensures the content is not revealed until the animation */
    border-right: 0.15em solid orange; /* The typwriter cursor */
    border-color: transparent;
    white-space: nowrap; /* Keeps the content on a single line */
    margin: 0 auto; /* Gives that scrolling effect as the typing happens */
    letter-spacing: 0.15em; /* Adjust as needed */
  }

  .windowContent > * {
    animation:
      typing 3s steps(80, end) forwards,
      blink-caret 0.75s step-end forwards;
  }

  @keyframes typing {
    from {
      width: 0;
    }
    to {
      width: 100%;
    }
  }

  @keyframes blink-caret {
    from,
    to {
      border-color: transparent;
    }
    50% {
      border-color: orange;
    }
  }
</style>
