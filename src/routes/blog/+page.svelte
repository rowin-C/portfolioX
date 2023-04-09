<script>
  import Back from "$lib/back.svelte";
  function onMouseHover() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 4;
  }
  function onMouseHover1() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 1;
  }
</script>

<div class="NA">
  <Back />
  <h1 on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}>
    Page under construction
  </h1>
  <p on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}>
    (centerd with only 2 lines of code)
  </p>
</div>

<style>
  .NA {
    color: white;
    height: 80vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .NA {
    animation: floatIn 0.5s ease-out;
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
</style>
