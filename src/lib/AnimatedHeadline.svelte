<script lang="ts">
  import { horizontalSlide } from "./transitions";
  import { cubicOut, cubicIn } from "svelte/easing";
  import { fly } from "svelte/transition";

  interface Props {
    texts?: string[];
    slide?: number;
    fade?: number;
    wait?: number;
    y?: number;
  }

  let {
    texts = ["text one", "text two", "text three"],
    slide = 200,
    fade = 300,
    wait = 1000,
    y = 6
  }: Props = $props();

  let currentIndex = $state(0);

  let timeout: string | number | NodeJS.Timeout | undefined;

  const next = () => {
    timeout = setTimeout(() => {
      if (texts.length === currentIndex + 1) currentIndex = 0;
      else currentIndex += 1;
      next();
    }, delay);
  };

  $effect(() => {
    next();
    return () => {
      clearTimeout(timeout);
    };
  });
  let delay = $derived(fade + slide + fade + wait);
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
