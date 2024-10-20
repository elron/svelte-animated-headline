[![Netlify Status](https://api.netlify.com/api/v1/badges/6fca70dc-1bdc-46a8-b30e-256e69b3c657/deploy-status)](https://app.netlify.com/sites/svelte-animated-headline/deploys)
![npm weekly downloads](https://img.shields.io/npm/dw/svelte-animated-headline)
![npm version](https://img.shields.io/npm/v/svelte-animated-headline)
![license](https://badgen.net/npm/license/svelte-animated-headline)

[DEMO](https://svelte-animated-headline.netlify.app/) | [REPL](https://svelte.dev/repl/1ac4e3559ac445ef984d312d632e6f02?version=3.46.4)


# Svelte Animated Headline

Add animated headline to your header banner, or anywhere else you want to grab attention in an informative way.

![Svelte Animated Headline Example](static/svelte-animated-headline.gif)


## Installation

```bash
# bun
bun i -D svelte-animated-headline // Svelte 5
bun i -D svelte-animated-headline@1.0.7 // Svelte 4
```
> bun is used here just as an example, you can use your package of choice (pnpm, npm, yarn)



## Usage

### 1. Import:
```html
<script>
  import { AnimatedHeadline } from "svelte-animated-headline";
</script>
```


### 2. Use:

```html
<AnimatedHeadline texts={["Change this", "to whatever", "you like!"]} />
```

## Props

### Settings
| Prop    |   Type	|   Description |	Default |
|---|---|---|---|
texts | `array[string]` | The text you want to animated | ["text one", "text two", "text three"]
  | wait | `number` | Wait duration between each item |  1000 
  | fade | `number` |  Duration of the fade/fly effect |  300 
  | slide | `number` | Duration of the slide effect (this occurs while the text is hidden) | 200 
  | y | `number` | The fly effect. Set it as 0 if you want only the fade effect. (Can be negative as well) | 6 |

> ### Note / Warning
> Each text will be shown as a single-line. No line break support.


## Examples

```html
<AnimatedHeadline
    texts={["No problem", "We can handle it", "Sure thing, honey", "Why not"]}
    y={0}
    wait={0}
    slide={1000}
    fade={500}
  />
```

```html
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
```

> For more code examples and playground: [REPL](https://svelte.dev/repl/1ac4e3559ac445ef984d312d632e6f02?version=3.46.4)


# Used by
[![ConfettiPage.io](static/confettipage-logo.png)](https://confettipage.io)

## License

[MIT license](https://opensource.org/license/mit/)

#### Publishing
(Dev note): To publish this library to [npm](https://www.npmjs.com):

```bash
pnpm publish
```


