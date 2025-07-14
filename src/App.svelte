<script>
  import { fade, fly } from "svelte/transition";

  import Image from "./lib/Image.svelte";
  let cardData = {};

  cardData["Reading"] = {
    image: "src/assets/light_bringer.jpg",
    title: "Reading",
    description:
      "I have loved reading since I was a little kid. I recently finished Light Bringer by Pierce Brown (amazing book) and I just started reading Project Hail Mary by Andy Weir.",
  };
  cardData["Baking"] = {
    image: "src/assets/brownies.jpg",
    title: "Baking",
    description:
      "Another one of my hobbies is baking! I especially enjoy making cookies and cakes.",
  };
  cardData["Traveling"] = {
    image: "src/assets/Travel.jpg",
    title: "Traveling",
    description:
      "I really enjoy traveling. I've visited California, Oregon, Pennsylvania, New Jersey, and North Carolina, and I've also technically been to Utah, Minnesota, and Illinois (layovers lol).",
  };
  cardData["Coding"] = {
    image: "src/assets/Keyboard.jpg",
    title: "Coding",
    description:
      "I love coding! My first introduction to programming was through Codecademy in 2017. There, I learned HTML and CSS and decided to major in Computer Science. I later attended KWK's 2020 web development camp that took place just before my senior year of high school. I initially heard about it from Tik Tok lol and actually applied on the last day that applications were open. I also attended KWK's 2021 Data Science camp. I learned Python, C++, Java, C, SQL, and JavaScript (and some JS frameworks) from several courses I took during high school and college. And here's a picture of the custom keyboard my brother made for me last Christmas :)",
  };
  cardData["Titus"] = {
    image: "src/assets/titus.jpg",
    title: "Titus",
    description:
      "This is my dog Titus! He is a 9 (almost 10) year old German Shepherd/Labrador Retriever/Border Collie mix. He's the sweetest boy and I love taking him out on walks.",
  };

  let fFacts = [
    "I worked in an optometry clinic for nearly 4 years.",
    "I was born and raised in Washington state.",
    "I'm a UW graduate :) I'm also the first of my siblings to go to university.",
  ];

  let name = "Abi Gutierrez"; // Change this to your name
  let bio = `My name is ${name} and I am 22, Salvadorian/Mexican, and recently graduated with a bachelor's degree in Computer Science and Systems. I am currently searching for a full-time software engineering position. I am also a 2-time Kode with Klossy alumni.`;
  let importantThings = ["Reading", "Baking", "Traveling", "Coding", "Titus"]; // List some hobbies

  let importantSelection = $state("Reading");
  let importantImage = $derived(cardData[importantSelection].image);
  let importantDescription = $derived(cardData[importantSelection].description);
</script>

<div class="container">
  <h1 in:fly={{ y: -200, duration: 2000 }}>About Me</h1>
  <p in:fly={{ y: 200, duration: 2000 }}>{bio}</p>

  <h2 in:fly={{ y: 200, duration: 2000 }}>Things I love</h2>
  <p in:fly={{ y: 200, duration: 2000 }}>
    Click one of the buttons below to learn more about my favorite things!
  </p>
  <div class="important-stuff" in:fly={{ y: 200, duration: 2000 }}>
    {#each importantThings as important}
      <button
        onclick={() => {
          importantSelection = important;
          importantImage = cardData[importantSelection].image;
          importantDescription = cardData[importantSelection].description;
        }}
        class="important"
        id={importantSelection}
        autofocus>{important}</button
      >
    {/each}

    <div class="card-container" in:fly={{ y: 200, duration: 2000 }}>
      <div class="card-inner">
        {#key importantSelection}
          <div
            class="theImage"
            in:fly={{ y: 50, duration: 1000 }}
            out:fade={{ duration: 100, delay: 0 }}
          >
            <Image
              image={importantImage}
              title={importantSelection}
              description={importantDescription}
            />
          </div>
        {/key}
      </div>
    </div>
  </div>

  <h2 in:fly={{ y: 600, duration: 2000 }}>Fun facts</h2>
  <div class="facts">
    <ol id="facts-list" in:fly={{ y: 600, duration: 2000 }}>
      {#each fFacts as fact}
        <li class="fact-description">{fact}</li>
      {/each}
    </ol>
  </div>
</div>

<!-- Set-ExecutionPolicy Unrestricted -Scope CurrentUser
http://localhost:5173/ 
use "npm run dev" to run project, then nav to link listed above -->

<style>
  h1 {
    color: rgb(161, 141, 236);
    opacity: 30%;
    font-family: Arial, sans-serif;
  }
  .container {
    max-width: 800px;
    margin: 0 auto;
    margin-bottom: 100px;
    padding: 20px;
    text-align: center;
    position:
      0,
      -200;
  }
  .important-stuff {
    display: flex;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;
  }
  .important {
    border-radius: 6px;
    border-color: rgb(161, 141, 236);
    background-color: rgb(7, 7, 23);
    color: rgb(211, 210, 210);
    padding: 10px 15px;
    transition-duration: 0.3s;
    box-shadow: 6px 6px 8px 2px black;
    font-weight: bold;
  }

  .important:hover {
    background-color: rgb(161, 141, 236);
    color: white;
  }

  .important:active,
  .important:focus {
    background-color: rgb(161, 141, 236);
  }

  .card-container {
    margin-top: 40px;
    margin-bottom: 40px;
  }

  .theImage {
    display: flex;
    justify-content: space-around;
  }
</style>
