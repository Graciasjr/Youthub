<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">	
	<Header/>
	<main>
		<slot/>
	</main>

</div>


<style>
	.app{
		width: 100%;
		height: 100vh;

	}

</style>
