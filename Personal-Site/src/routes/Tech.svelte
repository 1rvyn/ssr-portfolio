<script>
  let showDropdown = false;
  
  let selectedLang;
  let activeButton;
  
  const projects = {
    Go: [
      { name: "Authentication microservice", url: "https://github.com/1rvyn/backend-api", logo: "github-icon.png", description: "A go web-app to handle login/signup + other backend needs for my frontend honours project." },
      { name: "Endpoint-stresser", url: "https://github.com/1rvyn/endpoint-stresser", logo: "github-icon.png", description: "An endpoint stresser using Go-Routines to test my web-app scalability." },
    ],
    Node: [
      { name: "F1 data web app", url: "https://github.com/1rvyn/f1-data", logo: "github-icon.png", 
      description: "A web app that allows users to create matplotlib graphs/charts showing data from f1 races from a telemetry client."},
      { name: "Youtube data overhead viewer ", url: "https://github.com/1rvyn/", logo: "github-icon.png", 
      description: "A data visualisation tool that allows users to see semi-accurate caluclations on the amount of data they use on youtube. (repo has a private key inside it whoops)"},
    ],
    Svelte: [
      { name: "My portfolio", url: "https://github.com/1rvyn/ssr-portfolio", logo: "github-icon.png", description: "My portfolio website, built with SvelteKit." },
      { name: "TBD", url: "https://github.com/1rvyn/", logo: "github-icon.png", description: "My frontend for my honours project soon to be built with sveltekit" }

    ],
    Others: [
      { name: "RF-Letter-Recognition", url: "https://github.com/1rvyn/RF-Letter-recognotion", logo: "github-icon.png", description: "A random forest classifier to recognise letters from the MNIST dataset." },
      { name: "Sentiment Analysis", url: "https://github.com/1rvyn/sentiment_analysis", logo: "github-icon.png", description: "A large investigation into multiple AI models & pipelines & training methods to perform sentiment analysis (both keras & sklearn models)" },
      { name: "Game Collection", url: "https://github.com/1rvyn/GameCollection", logo: "github-icon.png", description: "A collection of games I have made in python using pygame. (Around 2018 @ college)" },
    ],
  };
  
  function toggleDropdown(lang) {
  showDropdown = !showDropdown;
  selectedLang = lang;

  if (showDropdown) {
    activeButton = lang;
  } else {
    activeButton = null;
  }
}

</script>

{#if showDropdown}
  <div class="dropdown fade-in">
    <h3 id={selectedLang}>My {selectedLang} projects</h3>
    {#each projects[selectedLang] as project}
    <div class="project">
      <a href={project.url} target="_blank" rel="noreferrer">
        <img src={project.logo} size =32x32 alt={project.name} />
        <span>{project.name}</span>
      </a>
      <p id="project-description">{project.description}</p>
    </div>
    {/each}
  </div>
{/if}

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div id="current-languages">
  I am currently working with<br>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class={activeButton === 'Go' ? 'lang-button active' : 'lang-button'} id="Go" on:click={() => toggleDropdown('Go')}>Go<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class={activeButton === 'Node.js' ? 'lang-button active' : 'lang-button'} id="Node" on:click={() => toggleDropdown('Node')}>Node.js<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class={activeButton === 'Svelte' ? 'lang-button active' : 'lang-button'} id="Svelte" on:click={() => toggleDropdown('Svelte')}>Svelte<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span id="intro-langes">and</span>
  <span class={activeButton === 'Others' ? 'lang-button active' : 'lang-button'} id="Others" on:click={() => toggleDropdown('Others')}>Others<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
</div>

<style>
  
  #project-description{
    color: white;
    font-weight: 100;
    padding: 0.5em 1em;
    text-align: left;
  }
  #current-languages {
    font-size: 1.5rem;
    font-weight: bold;
    color: white;
  }
  
  .lang-button {
    display: inline-block;
    cursor: pointer;
    position: relative;
  }
  
  .underline {
    display: block;
    height: 2px;
    margin: 0 auto;
    width: 0;
    transition: width .25s linear;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    opacity: 0;
  }
  
  #Go {
    color: #00ADD8;
  }
  
  #Go > .underline {
    background-color: #00ADD8;
  }
  
  #Node {
    color: #339933;
  }
  
  #Node > .underline {
    background-color: #339933;
  }
  
  #Svelte {
    color: #ff3e00;
  }
  
  #Svelte > .underline {
    background-color: #ff3e00;
  }
  
  #Others {
    color: #FFD500;
  }
  
  #Others > .underline {
    background-color: #FFD500;
  }
  
  .lang-button:hover > .underline {
    width: 100%;
    opacity: 1;
  }
  
  .dropdown {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -30%);
    background-size: cover;
    background-position: center;
    background-color: black;
    width: 65%;
    height: 55%;
    border-radius: 10px;
    box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.75);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 1s ease-in-out;
    z-index: 1;
    padding: 1rem;
    text-align: left;
    overflow: auto;
    max-height: 80%;
  }

  .dropdown.fade-in {
    opacity: 1;
  }

  .project a{
    color: white;
    text-decoration: none;
    font-size: 1.5rem;
    font-weight: bold;
  }
  .project img{
    width: 48px;
    height: 48px;
    margin-right: 0.3rem;
  }

  .active > .underline {
  width: 100%;
  opacity: 1;
}


  

</style>

  