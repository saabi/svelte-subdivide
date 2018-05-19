# svelte-subdivide

A component for building Blender-style layouts in Svelte apps.

## Installation

```bash
yarn add @sveltejs/svelte-subdivide
```


## Usage

```html
<Subdivide items={things} component={Pane} />

<script>
  import Subdivide from '@sveltejs/svelte-subdivide';
  import Pane from './Pane.html';

  export default {
    components: { Subdivide },

    data() {
      return {
        Pane
      };
    }
  };
</script>
```

The component constructor you supply to `<Subdivide>` will be instantiated for each cell of your layout. Typically, it would be a component that allows the user to select from a variety of different panes.

```html
<!-- Pane.html -->
<div>
  {#if selected}
    <svelte:component this={selected.component}/>
  {:else}
    {#each options as option}
      <button on:click="set({ selected: option })">
        {selected.label}
      </button>
    {/each}
  {/if}
</div>
```


## Configuring webpack

If you're using webpack with [svelte-loader](https://github.com/sveltejs/svelte-loader), make sure that you add `"svelte"` to [`resolve.mainFields`](https://webpack.js.org/configuration/resolve/#resolve-mainfields) in your webpack config. This ensures that webpack imports the uncompiled component (`src/index.html`) rather than the compiled version (`index.mjs`) — this is more efficient.

If you're using Rollup with [rollup-plugin-svelte](https://github.com/rollup/rollup-plugin-svelte), this will happen automatically.


## License

[LIL](LICENSE)