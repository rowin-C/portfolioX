<script lang="ts">
  import { page } from "$app/stores";
  import Cursor from "./Cursor.svelte";

  function menuHover1() {
    // @ts-ignore
    document.querySelector(".text-menu").style.transform =
      "scale(0.9) translate(-1rem, 0)  ";

    // @ts-ignore
    document.querySelector(".text-menu").style.opacity = "0.5";
    // @ts-ignore
    document.querySelector(".square1").style.transform =
      "scale(1.5) translate(0, 0) ";
    // @ts-ignore
    document.querySelector(".square2").style.transform =
      "scale(1.5) translate(0, 0) ";
  }

  function menuHover2() {
    // @ts-ignore
    document.querySelector(".text-menu").style.transform =
      "scale(1) translate(0, 0) ";
    // @ts-ignore
    document.querySelector(".text-menu").style.opacity = "1";
    // @ts-ignore
    document.querySelector(".square1").style.transform =
      "scale(1) translate(0, 0) ";
    // @ts-ignore
    document.querySelector(".square2").style.transform =
      "scale(1) translate(0, 0) ";
  }

  function onMouseHover() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 5;
  }
  function onMouseHover1() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 1;
  }
</script>

<div class="header">
  <div class="text">
    <span on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}
      >SAUBHAGYA</span
    >
  </div>
  <div class="menu">
    <div
      on:mouseenter={menuHover1}
      on:mouseleave={menuHover2}
      class="text-menu"
    >
      <a
        on:mouseenter={onMouseHover}
        on:mouseleave={onMouseHover1}
        class="text"
        href="/menu"
      >
        {#if $page.url.pathname === "/menu"}
          Back
        {:else}
          Menu
        {/if}
      </a>
    </div>

    <a on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1} href="/menu">
      <div class="square">
        <div
          on:mouseenter={menuHover1}
          on:mouseleave={menuHover2}
          class="square1"
        />
        <div
          on:mouseenter={menuHover1}
          on:mouseleave={menuHover2}
          class="square2"
        />
      </div>
    </a>
  </div>
</div>

<style>
  .header {
    width: 85vw;
    margin: 4.3rem 4rem 0 9rem;
    height: 13vh;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: fixed;
  }

  .menu {
    width: 8rem;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }
  .text {
    font-family: "rubik", sans-serif;
    color: #fff;
    font-size: 1.2rem;
    text-decoration: none;
  }
  .text-menu {
    font-family: "rubik", sans-serif;
    color: #fff;
    font-size: 0.9rem;
    transition: all 0.4s cubic-bezier(0.62, 0.42, 0, 1.03);
  }

  .square {
    display: flex;
    flex-direction: column;
  }

  .square1,
  .square2 {
    width: 1.5rem;
    height: 1.5rem;
    rotate: 45deg;
    background-color: rbg(20, 20, 20);
    border: 2px solid #fff;
    transition: all 0.4s cubic-bezier(0.62, 0.42, 0, 1.03);
  }
</style>
