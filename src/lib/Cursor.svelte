<script lang="ts">
  import { spring } from "svelte/motion";

  let position = { x: 0, y: 0 };
  let opacity = 0;

  const laggyPosition = spring(position, {
    stiffness: 0.1,
    damping: 0.5,
  });

  $: $laggyPosition = position;
</script>

<svelte:body
  on:mousemove={(e) => {
    position = { x: e.clientX, y: e.clientY };
    opacity = 1;
  }}
  on:mouseleave={() => (opacity = 0)}
/>

<div
  id="cursor"
  style:translate="calc({$laggyPosition.x}px - 35%) calc({$laggyPosition.y}px -
  35%)"
  style:opacity
/>
<div id="dot" style:translate="{position.x}px {position.y}px" style:opacity />

<style>
  #cursor {
    height: 30px;
    width: 30px;
    background: #fff;
    border-radius: 50%;

    position: fixed;
    left: 0;
    top: 0;
    z-index: 10000;

    pointer-events: none;
    opacity: 0;
    transition: scale 500ms ease;
    mix-blend-mode: difference;
  }

  #dot {
    height: 10px;
    width: 10px;
    background: rgb(255, 255, 255);
    border-radius: 50%;

    position: fixed;
    left: 0;
    top: 0;
    z-index: 11000;

    pointer-events: none;
    opacity: 0;
    transition: opacity 500ms ease;
    mix-blend-mode: difference;
  }
</style>
