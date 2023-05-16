<script>
  let showDropdown = false;
  
  let selectedLang;
  let activeButton;
  
  const projects = {
    Go: [
      { name: "Authentication microservice", url: "https://github.com/1rvyn/backend-api", logo: "github-icon32x.png", 
      description: "A go web-app to handle login/signup, code submission marking, data storage and more." 
    },
      { name: "Endpoint-stresser", url: "https://github.com/1rvyn/endpoint-stresser", logo: "github-icon32x.png", 
      description: "An endpoint stresser using Go-Routines to test web-app scalability + p99/p50 timings." 
    },
    { name: "LeetcodeEsque", url: "https://github.com/1rvyn/leetcode-esque", logo: "favicon-32x32.png", 
      description: "The front-end for my honours project, a leetcode-esque website to help practice coding problems. (watch the video in the readme to see it in action)" 
    },

    ],
    Node: [
      { name: "F1 data web app", url: "https://github.com/1rvyn/f1-data", logo: "github-icon32x.png", 
      description: "A web app that allows users to create matplotlib graphs/charts showing telemetry data from f1."},
      { name: "Youtube data overhead viewer ", url: "https://github.com/1rvyn/datavis-2", logo: "github-icon32x.png", 
      description: "A data visualisation tool that allows users to see semi-accurate caluclations on the amount of data channel's use on youtube. (needs facelift)"},
      {name: "Enterprise-web-system", url: "https://github.com/1rvyn/ent-web-system", logo: "github-icon32x.png",
      description: "A Golang backend with a react frontend which lets users create quotes for projects with a randomised fudge factor."},
      { name: "My portfolio", url: "https://github.com/1rvyn/ssr-portfolio", logo: "favicon-32x32.png",
       description: "My portfolio website, built with SvelteKit and hosted with Vercel." 
      }
    ],
    Python: [
      { name: "RF-Letter-Recognition", url: "https://github.com/1rvyn/RF-Letter-recognotion", logo: "github-icon32x.png",
       description: "A random forest classifier to recognise letters from the MNIST dataset." 
      },
      { name: "Sentiment Analysis", url: "https://github.com/1rvyn/sentiment_analysis", logo: "github-icon32x.png",
       description: "Using NLP to perform sentiment analysis (using both keras & sklearn models)" 
      },
      { name: "Game Collection", url: "https://github.com/1rvyn/GameCollection", logo: "github-icon32x.png",
       description: "A collection of games I have made in python using pygame."
       },
       { name: "Rat Maze Game", url: "https://github.com/1rvyn/Rat_Matrix_Maze", logo: "github-icon32x.png",
       description: "Another game made in college, a maze game where you play as a rat trying to get to the sprout."
       },
    ],
    Others: [
      { name: "f1 hub app", url: "https://github.com/1rvyn/F1HubApp", logo: "github-icon32x.png",
       description: "An android app which shows the latest f1 news, results, standings and the location of the race using google maps (to help plan trips to the venue)."
       },
       { name: "Misc technologies", url: "https://github.com/1rvyn/", logo: "github-icon32x.png",
        description: `Some of the other technologies I have used include: AWS, GCP, Azure, OVH, Kuberenetes, Docker, Git, Redis, PostgreSQL, MongoDB, MySQL, C#, C++.`
        },
      { name: "Codewars", url: "https://www.codewars.com", logo: "logo-codewars.svg",
      description: `I'm currently #1 place in my schools Codewars team where I practice algorithim questions.`
      }
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

function closeDropdown() {
  showDropdown = false;
}

</script>

{#if showDropdown}
  <div class="dropdown fade-in" id="myDropdown" >
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <i class="fas fa-times close-btn" on:click={closeDropdown}></i>

    <div class="content-container">
      <div class="header-container">
        <h3 id={selectedLang}>My {selectedLang} projects</h3>
      </div>
      <div class="projects-container">
        {#each projects[selectedLang] as project}
          <div class="project">
            <a href={project.url} target="_blank" rel="noreferrer">
              <div class="project-content">
                <img src={project.logo} size=32x32 alt={project.name} />
                <span>{project.name}</span>
              </div>
            </a>
            <p id="project-description">{project.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </div>
{/if}



<!-- svelte-ignore a11y-click-events-have-key-events -->
<div id="current-languages">
  I am currently working with<br>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class={activeButton === 'Go' ? 'lang-button active' : 'lang-button'} id="Go" on:click={() => toggleDropdown('Go')}>Go<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class={activeButton === 'Node.js' ? 'lang-button active' : 'lang-button'} id="Node" on:click={() => toggleDropdown('Node')}>Javascript<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class={activeButton === 'Python' ? 'lang-button active' : 'lang-button'} id="Python" on:click={() => toggleDropdown('Python')}>Python/AI + ML<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span id="intro-langes">and</span>
  <span class={activeButton === 'Others' ? 'lang-button active' : 'lang-button'} id="Others" on:click={() => toggleDropdown('Others')}>Other<span class="underline"></span></span>,  <!-- svelte-ignore a11y-click-events-have-key-events -->
</div>

<style>

.projects-container::-webkit-scrollbar {
    width: 8px;
  }

  .projects-container::-webkit-scrollbar-track {
    background-color: #38152A;
    border-radius: 10px;
  }

  .projects-container::-webkit-scrollbar-thumb {
    background-color: #00ADD8;
    border-radius: 10px;
  }


    .project {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-bottom: 1rem;
  }

  .close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  cursor: pointer;
  font-size: 1.5rem;
  color: #f5f5f5;
}

  .project-content {
    display: flex;
    align-items: center;
    margin-bottom: 0.5rem;
  }

  #project-description {
  color: #f5f5f5; 
  font-weight: 100;
  padding: 0.5em 1em;
  text-align: left;
  margin-bottom: 1rem;
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
  
  #Python {
    color: #339933;
  }
  
  #Python > .underline {
    background-color: #339933;
  }
  
  #Others {
    color: #ff3e00;
  }
  
  #Others > .underline {
    background-color: #ff3e00;
  }
  
  #Node {
    color: #FFD500;
  }
  
  #Node > .underline {
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
  background-color: #38152A; 
  width: 65%;
  height: 55%;
  border-radius: 10px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.75);
  display: flex;
  flex-direction: column;
  justify-content: center;
  opacity: 0;
  transition: opacity 1s ease-in-out;
  z-index: 1;
  padding: 1rem;
  text-align: left;
  overflow: auto;
  max-height: 80%;
  padding-left: 1rem;
  font-family: 'Inconsolata', monospace; 
}


  .content-container {
    display: flex;
    flex-direction: column;
    height: 100%;
  }

  .header-container {
    text-align: center;
    margin-bottom: 1rem;
  }

  .projects-container {
    overflow-y: auto;
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

  