<script>
  import Cursor from "./Cursor.svelte";

  function backZoom() {
    // @ts-ignore
    document.querySelector("#menu-bg-pattern").style.scale = 3;
  }
  function backZoom1() {
    // @ts-ignore
    document.querySelector("#menu-bg-pattern").style.translate = "400px 0px";
    // @ts-ignore
    document.querySelector("#menu-bg-pattern").style.scale = 4;
  }
  function onMouseHover() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 4;
  }
  function onMouseHover1() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 1;
  }
</script>

<Cursor />

<div on:mouseenter={backZoom} on:mouseleave={backZoom1} id="back">
  <div on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1} class="svg">
    <a href="/menu">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32"
        ><path
          d="M3.41 2H16V0H1a1 1 0 0 0-1 1v16h2V3.41l28.29 28.3 1.41-1.41z"
          data-name="7-Arrow Up"
        /></svg
      >
    </a>
  </div>
  <div>
    <a
      on:mouseenter={onMouseHover}
      on:mouseleave={onMouseHover1}
      class="text"
      href="/menu">Back</a
    >
  </div>
</div>

<style>
  #back {
    width: 10rem;
    display: flex;
    flex-direction: row;
    align-items: baseline;
    margin-top: 3rem;
    margin-left: 7rem;
  }

  svg {
    width: 3rem;
    height: 3rem;
    fill: white;
    margin-right: 1rem;
  }
  .text {
    font-size: 2rem;
    font-family: "rubik", sans-serif;
    color: white;
    text-decoration: none;
    z-index: 1;
  }
</style>
