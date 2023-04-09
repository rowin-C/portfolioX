<script lang="ts">
  import Back from "$lib/back.svelte";
  import Scrollbar from "smooth-scrollbar";
  //@ts-ignore
  //   Scrollbar.init(document.querySelector(".container"), options);
</script>

<div id="scroll" class="container">
  <Back />
  <div class="bg">
    <img src="/pp.jpg" alt="" />
    <span>HI HELLO HEHE </span>
  </div>
  <section class="body">
    <div class="left">
      <h1>About</h1>
    </div>
    <div class="right">
      <p>
        I enjoy the proccess of creating something which fuels my passion as an
        Artist. I'm a UI/UX designer and a Graphic designer as well.
      </p>
      <p>
        I have worked on many projects, which consist of developing a full
        fledged app UI for a SGD goal and also designing logos, posters,
        banners, flyers, brochures, business cards for the Inter IIIT sports
        Meet held at IIIT kancheepuram.
      </p>
      <p>
        Web dev or Graphic design are a way to express my creativity and i love
        it.
      </p>
      <p>
        Looking forward to work with people who share the same passion as me.
      </p>
    </div>
  </section>
</div>

<style>
  .bg {
    margin-top: 7rem;
    font-size: 18rem;
    font-style: italic;
    font-family: "Anton", sans-serif;
    opacity: 0.3;
    position: absolute;
    z-index: -1;
  }
  .body {
    color: rgb(255, 255, 255);
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: flex-start;
    height: 100vh;
    width: 100vw;
    font-family: "rubik", sans-serif;
  }
  .left {
    width: 90vw;
    position: fixed;
  }

  .right {
    width: 45vw;
    margin-left: 40rem;
  }
  .left h1 {
    margin-top: 2rem;
    margin-left: 5rem;
    margin-right: -10rem;
    font-size: 6rem;
  }

  p {
    font-family: "Inter", sans-serif;
    font-size: 2.5rem;
    font-weight: 500;
    margin-bottom: 10rem;
    margin-top: 10rem;
  }

  .container {
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

  button {
    font-size: 1.2rem;
    font-family: "rubik", sans-serif;
    font-weight: 500;
    background-color: rgb(20, 20, 20);
    height: 3rem;
    width: 10rem;
    border: solid 3px #5c060d;
    border-radius: 10px;
    box-shadow: 0px 0px 2px rgb(0, 0, 0);
    transition: all 300ms cubic-bezier(0.62, 0.42, 0, 1.03);
    margin-left: 3.5rem;
  }
  button a {
    color: white;
    text-decoration: none;
  }

  button:hover {
    transform: translateY(-5px);
    background-color: #ce1b26;
  }
</style>
