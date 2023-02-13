<script>
	import Header from './Header.svelte';
	import './styles.css';
	import Footer from './Footer.svelte';

</script>

<div class="layout-app">
	<Header />
	<main class="slot-content">
		<slot />
	</main>
	<Footer />
</div>

<style>
	.layout-app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}
	div.layout-app {
		background-color: #38152A; 
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	main.slot-content {
		display: none;
	}

</style>
