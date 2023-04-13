<script>
	import Header from './Header.svelte';
	import './styles.css';
	import SuggestionVideo from '$lib/components/SuggestionVideo.svelte';
	import PlaylistVideo from '$lib/components/PlaylistVideo.svelte';

	let suggestion = true;
</script>

<svelte:head>
	<title>WatchTube</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="app">	
	<nav>
		<Header/>
	</nav>
	<main>
		<section class="main-panel">
			<slot/>
		</section>
		<section class="playlist-panel">
			<div class="pp-header">
				<div class="btn">
					<button id="{suggestion?'active-btn':''}" on:click={()=>{suggestion=true}}>Suggestion</button>
					<button  id="{!suggestion?'active-btn':''}" on:click={()=>{suggestion=false}}>PlayList</button>
				</div>
			</div>
			<div class="panel-container">
				{#if suggestion}
					<section class="suggestion-video">
						<SuggestionVideo></SuggestionVideo>
					</section>
				{:else}
					<section class="playlist-video">
						<PlaylistVideo></PlaylistVideo>
					</section>
				{/if}
			</div>
		</section>
	</main>

</div>


<style>
	.app{
		width: 100%;
		min-height: 100vh;
		background:var(	--primary-bg-Color);
		display: flex;
		flex-direction: column;
		position: relative;
	}
	nav{
		width:100vw;
		height: auto;
		position: fixed;
		z-index:9999;
	}

	main{
		margin-top: 9vh;
		padding: 10px 7px 0 7px;
		width: 100%;
		min-height: 91vh;
		display: flex;
		justify-content: space-between;
		color: #fff;
	}

	button{
		cursor: pointer;
	}

	section{
		/* border: 1px solid #fff; */
	}

	.main-panel{
		width:/*870px*/73%;
	}

	.playlist-panel{
		border: 1px solid;
		width:/*300px*/27%;
		display: flex;
		flex-direction: column;
	}
	.pp-header{
		border: 1px solid;
		padding:12px 0;
		display: flex;
	}

	.pp-header .btn{
		/* border: 1px solid; */
		width: auto;
		display: flex;
		justify-content: center;
		/* padding: 3px 10px; */
		border-radius: 50px;
		margin-left: 2%;
		background: #ffffff10;
	}

	.pp-header button{
		border: 0px;
		padding: 6px 14px;
		background: transparent;
		color: #fff;
		font-weight: bold;
		transition: color 1s ease-out;
		border-radius: 50px;
	}

	.pp-header button:hover{
		text-decoration: underline;
	}
	
	#active-btn{
		background-color: #fafafa ;
		color: #000;
	}
	#active-btn:hover{
		text-decoration: none;
	}

	.suggestion-video{
		border: 1px solid royalblue;
		width: 100%;
		min-height: 80vh;
		display: flex;
		flex-direction: column;
		gap:2px;
		/* overflow-x: hidden; */
	}
</style>
