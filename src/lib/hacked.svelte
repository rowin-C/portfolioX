<script>
  let words = [
    "FRONTEND DEVELOPER",
    "SOFTWARE DEVELOPER",
    "UI/UX‎ ‎  DESIGNER",
  ];
  let word;
  let i = 1;
  const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

  let itretion = 0;
  function changeWords() {
    const interval = setInterval(() => {
      // @ts-ignore
      document.querySelector("#hacked").innerHTML = document
        .querySelector("#hacked")
        .innerHTML.split("")
        .map((letter, index) => {
          if (index < itretion)
            // @ts-ignore
            return document.querySelector("#hacked").dataset.value[index];

          return letters[Math.floor(Math.random() * 26)];
        })
        .join("");
      // @ts-ignore
      if (itretion >= document.querySelector("#hacked").innerHTML.length) {
        clearInterval(interval);
      }

      itretion += 1 / 2;
    }, 30);

    if (i >= 3) i = 0;
    word = words[i];
    i++;
    itretion = 0;
  }
</script>

<h1 id="hacked" on:mouseenter={changeWords} data-value={word}>
  FRONTEND DEVELOPER
</h1>

<style>
  h1 {
    width: 75vw;
    padding-left: 4rem;
    margin-left: 7rem;
    margin-top: 2rem;
    font-family: "Space Grotesk", sans-serif;
    color: #cecece;
    font-size: 6.5vw;
  }

  #hacked {
    transition: all 0.2s cubic-bezier(0.62, 0.42, 0, 1.03);
  }

  /* h1:hover {
    background-color: white;
    color: black;
  } */
</style>
