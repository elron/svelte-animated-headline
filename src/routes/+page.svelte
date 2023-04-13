<script>
  import AnimatedHeadline from "../lib/AnimatedHeadline.svelte";
</script>

<p>
  This can be <AnimatedHeadline
    texts={["very fast", "speedy", "quick"]}
    wait={0}
  />, believe it or not!
</p>

<hr />

<h1>
  Use this <AnimatedHeadline texts={["amazing", "incredible", "awesome"]} /> animated
  headline.
</h1>

<hr />

<h2>
  Just fade? <AnimatedHeadline
    texts={["No problem", "We can handle it", "Sure thing, honey", "Why not"]}
    y={0}
    wait={0}
    slide={1000}
    fade={500}
  />.
</h2>

<hr />

<h3>
  I <AnimatedHeadline
    texts={[
      "believe I can fly",
      "can touch the sky",
      "think about it every night and day",
      "spread my wings and fly away",
    ]}
    y={-80}
    fade={2300}
    slide={1000}
    wait={500}
  />... 🎵
</h3>

<hr />

<p>
  Just added <AnimatedHeadline
    texts={["1", "2", "3", "4", "5", "6", "7", "8"]}
    y={-3}
    wait={20}
    slide={0}
    fade={150}
  />/8 eggs and <AnimatedHeadline
    texts={["1", "2", "3"]}
    y={-3}
    wait={1500}
    slide={0}
    fade={150}
  />/3 cups of flower.
</p>

<style>
  :global(body) {
    text-align: center;
    padding: 3em;
    font-family: Arial, Helvetica, sans-serif;
  }
  hr {
    margin: 3.5em auto;
    width: 10%;
  }
</style>
