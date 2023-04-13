<script>
	import Fa from 'svelte-fa'
	import { faSearch, faMoon, faTriangleCircleSquare,faTriangleExclamation} from '@fortawesome/free-solid-svg-icons'
</script>


<header>
	<div class="logo">
		<div class="triangle"></div>
		<h2>WatchTube</h2>
	</div>
	<div class="seacher">
		<input type="text" placeholder="Search...">
		<button>
			<Fa icon={faSearch} color="#fff"></Fa>
		</button>
		
	</div>
	<div class="theme-switcher">
		<button>
			<Fa icon={faMoon} color="#fafafa"></Fa>
		</button>
	</div>
</header>


<style>

	
	header{
 		/* border: 1px solid #ccc; */
		/* position: fixed; */
        width: 100%;
        height: 9vh;
		padding:5px 10px ;
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 10px;
        background: var(--color3);
		color: var(--primary-color);
	}

	.logo{
		position: relative;
		padding: 0 5px;
		display: flex;
		align-items: center;
		font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
	}

	.logo .triangle{
		display: inline-block;
		width: 35px;
		height: 23px;
		position: relative;
		/* border-radius: 5px; */
		background: royalblue;
	}
	.logo .triangle::after{
		position: absolute;
		content: "";
		bottom:20%;
		left:35%;
		width: 0;
		border:7px solid transparent ;
		border-top: 0px;
		border-bottom:12px solid #fff;
		transform: rotate(90deg);
	}
	.logo h2{
		display: inline-block;
		font-size:27px;
		padding: 0 5px;
	}

	.seacher{
		width:400px;
		display: flex;
		position: relative;
		align-items: center;
		gap: 10px;
	}
	.seacher input{
        width:100%;
        height: 5vh;
        border: none;
        border-radius: 50px;
        padding-left: 13px;
		background:var(--color5);
		color: #fafafa;
		font-family: Calibri;
		font-size: 14px;
		outline: none;
    }

	.seacher input:focus{
        border: 2px solid #ffffff33;
		font-size: 14px;
        transition:border 0.3s ease-out;
    }

	.seacher input::placeholder{
		color: #fff;
	}

    .seacher button,
	.theme-switcher button{
		position: absolute;
		right:3%;
        width:25px;
        height:25px;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 0 20px;
		border-radius: 50px;
		background: /*var(--color5)*/#ffffff27;
        cursor: pointer;
        border: none;
		transition: all 0.3s ease-out;
    }
	
    header button:hover{
		background:#ffffff41 ;
	}

	.theme-switcher{
		/* border: 1px solid; */
		position: relative;
		width: 50px;
		height: 23px;
		margin-right: 25px;
	}

</style>