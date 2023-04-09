<script>
  import Back from "$lib/back.svelte";
  import { style } from "svelte-body";

  function onMouseHover() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 4;
  }
  function onMouseHover1() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 1;
  }
</script>

<Back />

<svelte:body use:style={{ overflow: "hidden" }} />

<section class="body">
  <div class="left">
    <h1>Contact</h1>
    <img class="image" src="/contact.gif" alt="" />
  </div>
  <div class="right">
    <h1>Lets' Chat</h1>
    <p>
      You wont get to know me until we talk so feel free to reach out to<br />
      discuss ideas, oppertunity,projects. Or if you just have questions or want
      to<br /> say hi, that's cool too.
    </p>
    <h2 on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}>
      👋<a href="mailto:cs20b1086@iiitdm.ac.in" target="_blank">
        cs20b1086@iiitdm.ac.in</a
      >
    </h2>
    <h3>Just wanna Chat ?</h3>
    <p>That's cool lets talk on telegram without sharing our info.</p>
    <button
      ><a href="https://t.me/ronwinner" target="_blank">Telegram</a></button
    >
  </div>
</section>

<style>
  .image {
    width: 25rem;
    height: 17rem;
    margin-left: 5rem;
  }
  .body {
    margin-top: 10rem;

    color: white;
    font-family: "rubik", sans-serif;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }

  .left {
    display: flex;
    flex-direction: column;
  }

  .left h1 {
    margin-top: -5rem;
    margin-left: 5rem;
    margin-right: -10rem;
    font-size: 6rem;
  }

  .right {
    margin-top: -20rem;
    margin-left: 17rem;
    height: 80rem;
    width: 50rem;
    padding: 3rem;
    color: black;
    background-color: white;
    border-radius: 2%;
  }
  .right h1 {
    margin-top: 13rem;
    font-size: 3rem;
  }
  .right p {
    font-size: 1.3rem;
  }
  .right h3 {
    font-size: 1.4rem;
    margin-top: 3rem;
  }
  a {
    text-decoration: none;
  }

  button {
    font-size: 1.2rem;
    font-family: "rubik", sans-serif;
    font-weight: 500;
    background-color: #7a4fee;
    height: 3rem;
    width: 20rem;
    border: solid 1px #7a4fee;
    border-radius: 2%;
    box-shadow: 0px 0px 2px rgb(0, 0, 0);
    transition: all 300ms cubic-bezier(0.62, 0.42, 0, 1.03);
  }
  button a {
    color: white;
    text-decoration: none;
  }

  button:hover {
    transform: translateY(-5px);
    background-color: rgb(20, 20, 20);
  }

  section {
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
