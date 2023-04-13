<script lang="ts">
  import { horizontalSlide } from "./transitions";
  import { cubicOut, cubicIn } from "svelte/easing";
  import { fly } from "svelte/transition";
  import { onMount } from "svelte";

  export let texts = ["text one", "text two", "text three"];
  export let slide = 200;
  export let fade = 300;
  export let wait = 1000;
  $: delay = fade + slide + fade + wait;
  export let y = 6;

  let currentIndex = 0;

  let timeout: number | undefined;

  const next = () => {
    timeout = setTimeout(() => {
      if (texts.length === currentIndex + 1) currentIndex = 0;
      else currentIndex += 1;
      next();
    }, delay);
  };

  onMount(() => {
    next();
    return () => {
      clearTimeout(timeout);
    };
  });
</script>

{#each texts as text, i}
  {#if currentIndex === i}
    <span
      transition:horizontalSlide={{ axis: "x", duration: slide, delay: fade }}
    >
      <span
        in:fly={{ y: y, duration: fade, delay: slide + fade, easing: cubicOut }}
        out:fly={{ y: 0 - y, duration: fade, delay: 0, easing: cubicIn }}
      >
        {text}
      </span>
    </span>
  {/if}
{/each}

<style>
  span {
    white-space: nowrap;
    display: inline-flex;
    width: fit-content;
    /* 		border: 1px solid teal;
		padding: 5px 10px;
		margin: 10px 20px; */
  }
</style>
