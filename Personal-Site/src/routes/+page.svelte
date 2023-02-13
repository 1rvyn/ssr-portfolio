<script>
    import Homecontent from './Homecontent.svelte';
	import Age from './Age.svelte';
	import Tech from './Tech.svelte';
	import Commits from './Commits.svelte';
</script>
<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Inconsolata&display=swap" rel="stylesheet">
	<link href="https://fonts.googleapis.com/css2?family=Playfair+Display&display=swap" rel="stylesheet">
	<script src="https://kit.fontawesome.com/83e9aaac76.js" crossorigin="anonymous"></script>
</svelte:head>
<section class="content">
	<div id="home-container">
		<p id="age-counter">I'm <Age/> years old</p>
		<Tech />
		<Homecontent />
		<Commits />

	</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;

	}

	#home-container {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		font-family: 'Inconsolata', monospace;
	}

	#age-counter {
		font-size: 1.5rem;
		padding-top: 2.5rem;
		font-weight: bold;
	}

</style>
