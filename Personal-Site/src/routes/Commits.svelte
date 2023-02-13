<script>
  import { onMount } from 'svelte';

  let commits = [];

  onMount(() => {
    fetch('https://api.github.com/users/1rvyn/events/public')
      .then(response => response.json())
      .then(data => {
        commits = data.filter(event => event.type === 'PushEvent')
          .slice(0, 5)
          .map(event => ({
            message: event.payload.commits[0].message,
            repo: event.repo.name,
            language: null,
            sha: event.payload.commits[0].sha
          }));
        fetchLanguages();
      });
  });

  function fetchLanguages() {
    commits.forEach((commit, index) => {
      const [owner, repo] = commit.repo.split('/');
      fetch(`https://api.github.com/repos/${owner}/${repo}/languages`)
        .then(response => response.json())
        .then(data => {
          const languages = Object.keys(data);
          commit.language = languages.length > 0 ? languages[0] : null;
          commits[index] = commit;
        });
    });
  }
</script>

<style>
  a.language {
    color:RED;
  }
  a.language.Go {
    color: #00ADD8;
  }
  a.language.Python {
    color: #a5a335;
  }
  a.language.JavaScript {
    color: #f1e05a;
  }
  a.language.HTML {
    color: #e34c26;
  }
  a.language.C {
    color: #555555;
  }
  a.language.Rust {
    color: #dea584;
  }
  a.language.TypeScript {
    color: #2b7489;
  }
  a.language.Svelte {
    color: #ff3e00;
  }
  a.language.Ejs {
    color: #a91e50;
  }
</style>

  <p id ="commit-text">Last seen commits<br>
  {#each commits as commit, index}
    {#if commit.language}
      <a href={`https://github.com/${commit.repo}/commit/${commit.sha}`}
         class={`language ${commit.language}`}>
        {commit.language}
      </a>
      {#if index !== commits.length - 1}, {/if}
    {/if}
  {/each}
</p>