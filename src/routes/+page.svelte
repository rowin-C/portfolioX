<script lang="ts">
  import { browser } from "$app/environment";
  import Cursor from "$lib/Cursor.svelte";
  import Hacked from "$lib/hacked.svelte";
  import Navbar from "$lib/navbar.svelte";
  import { onMount } from "svelte";
  import { expoOut } from "svelte/easing";
  import type { TransitionConfig } from "svelte/transition";
  import "../app.css";

  let loaded = false;

  let prefersReducedMotion = browser
    ? window.matchMedia("(prefers-reduced-motion: reduce)").matches
    : true;

  let word1Hovered = 0;
  let word2Hovered = 0;
  let word3Hovered = 0;
  let word4Hovered = 0;
  let word5Hovered = 0;
  let word6Hovered = 0;
  let word7Hovered = 0;

  $: complete =
    word1Hovered +
    word2Hovered +
    word3Hovered +
    word4Hovered +
    word5Hovered +
    word6Hovered +
    word7Hovered;

  $: if (complete === 7) {
    // @ts-ignore
    document.querySelector(".center").style.margin = "0 0 0 -10rem";
  }

  function wordIn(
    node: HTMLElement,
    { duration = 1500 } = {}
  ): TransitionConfig {
    return {
      // t + u = 1
      css: (t, u) => `
				transform: scale(${prefersReducedMotion ? 1 : 0.5 + t / 2});
				opacity: ${t};
			`,
      easing: expoOut,
      duration,
    };
  }

  function onMouseHover() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 4;
  }

  function onMouseHover1() {
    // @ts-ignore
    document.querySelector("#cursor").style.scale = 1;
  }

  onMount(() => (loaded = true));
</script>

<svelte:head>
  <title>Hello hello hello</title>
</svelte:head>

<Navbar />

<Cursor />

<div class="container">
  <section class="page1">
    <div class="center zoom-out">
      {#if loaded}
        <div class="text">
          <div class="line">
            <p
              class="word th1"
              in:wordIn={{ duration: 1000 }}
              class:hover={word1Hovered}
              class:motion={!prefersReducedMotion}
              on:pointerenter={() => (word1Hovered = 1)}
            >
              <span class="letter">H</span>
              <span class="letter">i</span>
              <span class="letter">,</span>
            </p>
            <p
              class="word th2"
              in:wordIn={{ duration: 1500 }}
              class:motion={!prefersReducedMotion}
              class:hover={word2Hovered}
              on:pointerenter={() => (word2Hovered = 1)}
            >
              <span class="letter">I</span>
              <span class="letter">'</span>
              <span class="letter">m</span>
            </p>
          </div>
          <div class="line">
            <p
              class="word names th3"
              in:wordIn={{ duration: 900 }}
              class:motion={!prefersReducedMotion}
              class:hover={word3Hovered}
              on:pointerenter={() => (word3Hovered = 1)}
            >
              <span class="letter">s</span>
              <span class="letter">a</span>
              <span class="letter">u</span>
              <span class="letter">b</span>
              <span class="letter">h</span>
              <span class="letter">a</span>
              <span class="letter">g</span>
              <span class="letter">y</span>
              <span class="letter">a</span>
            </p>
          </div>
          <div class="line">
            <p
              class="word th4"
              in:wordIn={{ duration: 500 }}
              class:motion={!prefersReducedMotion}
              class:hover={word4Hovered}
              on:pointerenter={() => (word4Hovered = 1)}
            >
              <span class="letter">a</span>
              <span class="letter">n</span>
              <span class="letter">d</span>
            </p>

            <p
              class="word th5"
              in:wordIn={{ duration: 1100 }}
              class:motion={!prefersReducedMotion}
              class:hover={word5Hovered}
              on:pointerenter={() => (word5Hovered = 1)}
            >
              <span class="letter">i</span>
            </p>
          </div>
          <div class="line love">
            <p
              class="word th6"
              in:wordIn={{ duration: 1000 }}
              style="color: #ff0000"
              class:motion={!prefersReducedMotion}
              class:hover={word6Hovered}
              on:pointerenter={() => (word6Hovered = 1)}
            >
              <span class="letter">l</span>
              <span class="letter">o</span>
              <span class="letter">v</span>
              <span class="letter">e</span>
            </p>
          </div>
          <div class="line tet">
            <p
              class="word fancy th7"
              in:wordIn={{ duration: 300 }}
              class:hover={word7Hovered}
              class:motion={!prefersReducedMotion}
              on:pointerenter={() => (word7Hovered = 1)}
            >
              <span class="letter">w</span>
              <span class="letter">h</span>
              <span class="letter">a</span>
              <span class="letter">t</span>
            </p>
            <p
              class="word fancy th8"
              in:wordIn={{ duration: 100 }}
              class:hover={word7Hovered}
              class:motion={!prefersReducedMotion}
              on:pointerenter={() => (word7Hovered = 1)}
            >
              <span class="letter" />
              <span class="letter" />
              <span class="letter">i</span>
              <span class="letter" />
              <span class="letter">d</span>
              <span class="letter">o</span>
              <span class="letter">.</span>
            </p>
          </div>
        </div>
      {/if}
    </div>
  </section>

  <section>
    <div class="page2">
      <div class="front"><span>I'm a</span></div>
      <div class="back" />
      <Hacked />
      <!-- <Test /> -->
      <button
        on:mouseenter={onMouseHover}
        on:mouseleave={onMouseHover1}
        class="move-now"><a href="/about/resume.pdf" download>Resume</a></button
      >
    </div>
  </section>
</div>

<section class="projects">
  <h1>PROJECTS</h1>
  <h1
    on:click={() => (window.location.href = "https://github.com/rowin-C")}
    on:mouseenter={onMouseHover}
    on:mouseleave={onMouseHover1}
    style="margin-top: -20px; display: flex; flex-direction: column; align-items: center;"
  >
    <span style="font-size: 20px;"
      >All my latest projects are updated in github ↗</span
    >
  </h1>

  <div class="proC">
    <div class="project">
      <div style="width: 30%;" class="content-text">
        <span>e-Patra</span>
        <p>
          A secure email service that protect your communications from prying
          eyes. With features like End-to-end encryption,Unlimited storage,
          Premium free of cost and Compatibility with PGP
        </p>

        <button on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}
          ><a href="https://e-patra.com" target="_blank"
            >Check it out
          </a></button
        >
      </div>
      <div class="zoom"><img class="imageH" src="/e_patra.png" alt="" /></div>
    </div>
    <div class="project">
      <div class="zoom">
        <img class="image" src="/urgent.png" alt="" />
      </div>
      <div class="conetent-text">
        <span>UI Design</span>
        <p>App for the management of solar panel at home</p>
        <p>
          BrightVolt App is used to see all the necessary<br /> information
          about the panels as well as help<br /> in making the right decision
          for the optimum<br /> energy saving
        </p>
        <button on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}
          ><a
            href="https://www.figma.com/file/NKwAWuBX9DiY7feUwT0QBt/Untitled?t=hHCcb0YGYiSUcvBV-0"
            target="_blank"
            >View in Figma
          </a></button
        >
      </div>
    </div>
    <div class="project">
      <div class="content-text">
        <span>Personalized AI Chat-bot </span>
        <p>
          Custom data embedding into supabase through<br /> OpenAi’s ada model
        </p>
        <p>Interface on React and Material UI library</p>
        <button on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}
          ><a
            href="https://open-ai-react-mui-personal-chat-assistant-rowinc.vercel.app/"
            target="_blank"
            >Check it out
          </a></button
        >
      </div>
      <div class="zoom"><img class="imageH" src="/chatbot.png" alt="" /></div>
    </div>
    <div class="project">
      <div class="zoom"><img class="imageH" src="/blog.png" alt="" /></div>
      <div class="conetent-text">
        <span>React NextJs Blog</span>
        <p>Blog Page with multiple page Routing</p>
        <p>Modern UI design with react components</p>

        <button on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}
          ><a href="https://blog-rowinc.vercel.app/" target="_blank"
            >View Site
          </a></button
        >
      </div>
    </div>

    <div class="project">
      <div style="width: 30%;" class="content-text">
        <span>Up Up </span>
        <p>
          Its a endless runner game coded in C# in which character is my friend
        </p>

        <button on:mouseenter={onMouseHover} on:mouseleave={onMouseHover1}
          ><a href="https://github.com/rowin-C/Up_Up" target="_blank"
            >View in Github
          </a></button
        >
      </div>
      <div class="zoom"><img class="imageH" src="/upup.png" alt="" /></div>
    </div>
  </div>
</section>

<footer>
  <div class="stack">
    <a
      on:mouseenter={onMouseHover}
      on:mouseleave={onMouseHover1}
      href="https://www.instagram.com/saubhagya.prasad/"
      target="_blank"><img class="logo" src="/iglogo.png" alt="" /></a
    >
    <a
      on:mouseenter={onMouseHover}
      on:mouseleave={onMouseHover1}
      href="https://github.com/rowin-C"
      target="_blank"><img class="logo" src="/gitlogo.png" alt="" /></a
    >
    <a
      on:mouseenter={onMouseHover}
      on:mouseleave={onMouseHover1}
      href="https://www.linkedin.com/in/saubhagya-prasad-8bb40724a/"
      target="_blank"><img class="logo smol" src="/linklogo.png" alt="" /></a
    >
  </div>
  <div class="made-text">
    <span
      >Made with <a
        on:mouseenter={onMouseHover}
        on:mouseleave={onMouseHover1}
        href="">❤️</a
      >
    </span>
    <span>by saubhagya</span>
  </div>
  <div class="blanck" />
</footer>

<style>
  .made-text a {
    text-decoration: none;
  }
  .move-now {
    margin-left: 11rem;
  }
  footer {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin: 0 5rem 3rem 5rem;
  }
  .smol {
    scale: 0.9;
  }

  .made-text {
    font-size: 2rem;
    font-family: "rubik", sans-serif;
    color: #cecece;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    height: 5rem;
  }
  .logo {
    height: 5rem;
    width: 5rem;

    margin: 1rem;
  }
  .project {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    margin-bottom: 10rem;
  }
  img {
    object-fit: cover;
    border-radius: 10px;
  }
  .imageH {
    height: 20rem;
    width: 30rem;

    scale: 1.1;
  }
  .image {
    height: 35rem;
    width: 20rem;
    scale: 1.2;
  }
  .proC {
    margin-top: 10rem;
  }
  .proC span {
    color: #cecece;
    font-size: 2.5rem;
    font-family: "rubik", sans-serif;
    margin-left: 5rem;
    opacity: 1;
  }
  .proC p {
    color: #cecece;
    font-size: 1.5rem;
    font-family: "rubik", sans-serif;
    margin-left: 5rem;

    opacity: 1;
  }

  .projects {
    margin-top: 30rem;
  }
  .projects h1 {
    margin-top: 10rem;
    display: flex;
    justify-content: center;
    font-size: 4rem;
    color: #cecece;
    font-family: "rubik", sans-serif;
  }

  button {
    margin: 2rem 0 0 5rem;
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
  .page1 {
    padding: 15rem 0;
    height: 100vh;
  }

  .page1 p {
    color: #cecece;
    font-size: 6vw;
    font-family: "rubik", sans-serif;
    margin: 0rem;
    text-transform: uppercase;
    opacity: 1;

    /* if not working on site take link from google fonts  */
  }

  .names {
    font-size: 6vw;
  }

  .text {
    width: 49vw;
    margin-top: 2rem;
    margin-left: 4rem;
  }
  .center {
    display: flex;
    align-items: center;
    justify-content: center;
    transition: margin 1150ms cubic-bezier(0.62, 0.42, 0, 1.03);
  }

  .line {
    display: flex;
    justify-content: space-between;
  }

  .love {
    display: flex;
    justify-content: flex-end;
    margin-right: -2rem;
  }

  .page2 {
    margin-top: 10rem;
    margin-bottom: 10rem;
  }

  .front {
    display: flex;
    width: 31vw;
    justify-content: center;
    font-family: "rubik", sans-serif;
    color: #cecece;
    font-size: 3.5vw;
  }
  .back {
    display: flex;
    width: 90vw;
    justify-content: center;
    font-family: "Space Grotesk", sans-serif;
    color: #cecece;
    font-size: 6.5vw;
  }

  .word > .letter {
    display: inline-block;
    transition: transform 1s ease;
  }

  .word.hover > .letter {
    transition-duration: 800ms;
  }

  .letter {
    padding: 0;
    margin: 0;
  }

  .word.motion > .letter:nth-child(1) {
    transform: translate(114%, 62%) rotate(-33deg);
  }

  .word.hover > .letter:nth-child(1) {
    transform: translate(0%, 0%) rotate(0deg);
    opacity: 1;
  }

  .word.motion > .letter:nth-child(2) {
    transform: translate(-512%, -38%) rotate(17deg);
  }

  .word.hover > .letter:nth-child(2) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(3) {
    transform: translate(-425%, -47%) rotate(-10deg);
  }

  .word.hover > .letter:nth-child(3) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(4) {
    transform: translate(336%, -125%) rotate(-8deg);
  }

  .word.hover > .letter:nth-child(4) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(5) {
    transform: translate(-1%, 64%) rotate(11deg);
  }

  .word.hover > .letter:nth-child(5) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(6) {
    transform: translate(-329%, -7%) rotate(8deg);
  }

  .word.hover > .letter:nth-child(6) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(7) {
    transform: translate(316%, -6%) rotate(8deg);
  }

  .word.hover > .letter:nth-child(7) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(8) {
    transform: translate(130%, -154%) rotate(8deg);
  }

  .word.hover > .letter:nth-child(8) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(9) {
    transform: translate(-290%, -20%) rotate(8deg);
  }

  .word.hover > .letter:nth-child(9) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(10) {
    transform: translate(-936%, 105%) rotate(8deg);
  }

  .word.hover > .letter:nth-child(10) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(11) {
    transform: translate(-600%, 141%) rotate(-24deg);
  }
  .word.hover > .letter:nth-child(11) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(12) {
    transform: translate(-500%, 63%) rotate(-79deg);
  }
  .word.hover > .letter:nth-child(12) {
    transform: translate(0%, 0%) rotate(0deg);
  }

  .word.motion > .letter:nth-child(13) {
    transform: translate(-24%, 122%) rotate(8deg);
  }
  .word.hover > .letter:nth-child(13) {
    transform: translate(0%, 0%) rotate(0deg);
  }

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
</style>
