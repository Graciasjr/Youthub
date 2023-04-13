<script>
	import Logo from "./material/Logo.svelte";
	import Fa from 'svelte-fa';
	import { faListDots} from '@fortawesome/free-solid-svg-icons'

</script>

<div class="video-snippet">
	<a href="/watch/" class="thumbnail">
		<div class="logo">
			<Logo></Logo>
		</div>
		<div class="video-info">
			<h3 >How to made your Vlog post Succesfully lsdkl smldk</h3>
			<span class="channel">Gracias_Jr</span>
		</div>
		<span class="video-time">00:00</span>
	</a>    
</div>


<style>

    .video-snippet{
		/* border: 1px solid #ccc; */
		width: 223px;
		height:123px;
		display: flex;
		flex-direction: column;
		position: relative;
		
	}

	a{
		display:block;
		width: 100%;
		height: 100%;
		background:/*#000*/#fff;
		position:relative;
		text-decoration: none;
		transition:all 0.3s ease-out;
		border-radius: 3px;
	}
		
	.logo{
		position: absolute;
		top:34%;
		left: 43%;
		z-index:2;
		/* display: none; */
	} 

	a:hover{
		filter: blur(1px);
		/* border-radius: 7px; */
	}
	a:hover .logo{
		display: block;
		transition: all 1s ease-out;
	}
	

	a:hover::after{
		/* border: 1px solid crimson; */
		position: absolute;
		content: "";
		top: 0;
		z-index: 1;
		width: 100%;
		height: 100%;
		background: #00000050;
		transition:0.3s ease-out;

	}	

	.video-info{
		/* border: 1px solid; */
		position: absolute;
		bottom: 0;
		width: 100%;
		height:45px ;
		color: #000;
		padding: 0 0 5px 10px;
		font-size: 14px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: self-start;
		font-weight: none;
		background: transparent;
		
	}

	.video-info h3{
		font-size: 12px;
		width:210px;
		color: #000;
		overflow-x: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
	}

	.channel{
		font-size:11.5px;
		padding:2px 10px ;
		font-weight: bold;
		background:hsl(225, 73%, 90%)/*#4169e13a*/;
		color: #333;
		border-radius:3px;
	}

	.video-time{
		/* border: 1px ; */
		position: absolute;
		font-weight: bold;
		font-size: 12px;
		bottom: 4px;
		right: 7px;
		padding: 2px 5px;
		cursor: none;
		background: #eee;
		color: /*#4b4a4a*/#333;
		border-radius: 7px;
		text-align: center;
	}
	

	
</style>