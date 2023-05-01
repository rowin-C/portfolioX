<script lang="ts">
  import Cursor from "$lib/Cursor.svelte";
  import { style } from "svelte-body";

  let bgTranslateY = 0;
  let bgScale = 4;
  let bgOpacity = 0.2;

  function onMouseHover() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 4;
  }
  function onMouseHover1() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 1;
  }

  function onMouseHover2() {
    bgTranslateY = -200;
  }

  function onMouseHover3() {
    bgTranslateY = -400;
  }

  function onMouseHover4() {
    bgTranslateY = -600;
  }

  function onMouseHover5() {
    bgTranslateY = -700;
  }

  function hoverIn() {
    bgScale = 3;
    bgOpacity = 0.1;
  }

  function hoverOut() {
    bgScale = 4;
    bgOpacity = 0.2;
  }
</script>

<svelte:body use:style={{ overflow: "hidden" }} />

<Cursor />

<div class="container">
  <div class="" id="menu">
    <div class="" id="menu-items">
      <a
        on:mouseenter={onMouseHover}
        on:mouseleave={onMouseHover1}
        on:mouseenter={onMouseHover2}
        on:mouseenter={hoverIn}
        on:mouseleave={hoverOut}
        href="/"
        class="menu-item">Home</a
      >
      <a
        on:mouseenter={onMouseHover}
        on:mouseenter={onMouseHover3}
        on:mouseleave={onMouseHover1}
        on:mouseenter={hoverIn}
        on:mouseleave={hoverOut}
        rel="noreferrer"
        target="_blank"
        href="https://blog-rowinc.vercel.app/"
        class="menu-item">Blog</a
      >
      <a
        on:mouseenter={onMouseHover}
        on:mouseenter={onMouseHover4}
        on:mouseleave={onMouseHover1}
        on:mouseenter={hoverIn}
        on:mouseleave={hoverOut}
        href="/about"
        class="menu-item">About</a
      >
      <a
        on:mouseenter={onMouseHover}
        on:mouseenter={onMouseHover5}
        on:mouseleave={onMouseHover1}
        on:mouseenter={hoverIn}
        on:mouseleave={hoverOut}
        href="/contact"
        class="menu-item">Contact</a
      >
    </div>
  </div>
</div>
<div
  class=""
  id="menu-bg-pattern"
  style:translate="0 {bgTranslateY}px"
  style:opacity={bgOpacity}
  style:scale={bgScale}
/>
<div class="menu-bg-image" />

<style>
  /* .menu-bg-image {
    background-image: url("../../../static/menu_back.jpg");
    z-index: 10;
  } */

  #menu {
    margin-top: 5rem;
    height: 100vh;
    display: flex;
    align-items: center;
  }
  #menu-items {
    width: 10rem;
    margin-top: -10rem;
    margin-left: 20rem;
    z-index: 0;
  }

  .menu-item {
    color: white;
    font-size: 5rem;
    font-family: "rubik", sans-serif;
    display: block;
    text-decoration: none;

    padding-bottom: 1rem;
    transition: all 400ms cubic-bezier(0.62, 0.42, 0, 1.03);
  }

  #menu-bg-pattern {
    height: 100vh;
    width: 100vw;

    background-color: #000000;
    opacity: 0.8;
    background-color: #000000;
    opacity: 0.8;
    background-color: #000000;
    opacity: 0.8;
    background: radial-gradient(
        circle,
        transparent 20%,
        #000000 20%,
        #000000 80%,
        transparent 80%,
        transparent
      ),
      radial-gradient(
          circle,
          transparent 20%,
          #000000 20%,
          #000000 80%,
          transparent 80%,
          transparent
        )
        100px 100px,
      linear-gradient(#ffffff 8px, transparent 8px) 0 -4px,
      linear-gradient(90deg, #ffffff 8px, #000000 8px) -4px 0;
    background-size: 200px 200px, 200px 200px, 100px 100px, 100px 100px;
    opacity: 0.2;
    scale: 4;

    position: absolute;
    left: 0;
    top: 0;

    z-index: -1;
    transition: all 600ms cubic-bezier(0.62, 0.42, 0, 1.03);
  }

  #menu-items:hover > .menu-item {
    opacity: 0.3;
  }
  #menu-items:hover > .menu-item:hover {
    opacity: 1;
  }

  /* .menu-item:hover {
    margin-left: 2rem;
    scale: 1.5;
  } */

  .container {
    animation: floatIn 0.3s ease-in-out;
  }

  @keyframes floatIn {
    0% {
      opacity: 0;
      transform: translateY(20px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }

  #menu-bg-pattern {
    animation: floatIn2 0.4s ease-in-out;
  }
  @keyframes floatIn2 {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 0.2;
    }
  }
</style>
