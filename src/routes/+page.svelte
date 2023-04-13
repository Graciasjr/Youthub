<script>
	import SnippetVideo from "$lib/components/SnippetVideo1.svelte";

	let videos = [
		{
			"kind": "youtube#searchResult",
			"id": {
				"kind": "youtube#video",
				"videoId": "PiX_y7DlbJU"
			},
			"snippet": {
				"publishedAt": "2023-03-22T13:15:05Z",
				"channelId": "UCk35YdCoXoFSEEiU-MUeMAQ",
				"title": "2023 New Songs ( Best English Songs 2023 ) 🥒 Pop Music 2023 New Songs 🍀 New Popular Songs 2023",
				"description": "2023 New Songs ( Best English Songs 2023 ) Pop Music 2023 New Songs New Popular Songs 2023 Thanks for watching ...",
				"thumbnails": {
					"default": {
						"url": "https://i.ytimg.com/vi/PiX_y7DlbJU/default.jpg",
						"width": 120,
						"height": 90
					},
					"medium": {
						"url": "https://i.ytimg.com/vi/PiX_y7DlbJU/mqdefault.jpg",
						"width": 320,
						"height": 180
					},
					"high": {
						"url": "https://i.ytimg.com/vi/PiX_y7DlbJU/hqdefault.jpg",
						"width": 480,
						"height": 360
					}
				},
				"channelTitle": "Pop internacional",
				"liveBroadcastContent": "none",
				"publishTime": "2023-03-22T13:15:05Z"
			}
    	}
		
	]
	
</script>



<main>	
	<SnippetVideo></SnippetVideo>
	<SnippetVideo></SnippetVideo>
	<SnippetVideo></SnippetVideo>
	<SnippetVideo></SnippetVideo>
	<SnippetVideo></SnippetVideo>
	<SnippetVideo></SnippetVideo>
	<SnippetVideo></SnippetVideo>
</main>


<style>
	main{
		border: 1px solid red;
		width: 97%;
		/* height: 100%; */
		margin: 0 auto;
		display:flex;
		flex-wrap: wrap;
		gap: 17px;
		padding: 2% 0 0 10px;
		/* position: relative; */
		
	}

	
	

	

</style>
