<script>

</script>


<header>
	<input type="text">
	<button>Rechercher</button>
</header>


<style>
	header{
 		border: 1px solid #ccc;
        width: 100%;
        height: 9vh;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 10px;
        background: #ddd;
	}

	header input{
        width:300px;
        height: 5vh;
        border: none;
        border-radius: 50px;
        padding-left: 12px;
        transition:all 0.1s ease-out;
    }

	header input:focus{
        outline: none;
        border: 2px solid royalblue;
        font-family: Calibri;
        font-size: 14px;
    }

    header button{
        width: 100px;
        height:4vh;
        font-weight: bold;
        color: #fafafa;
        background: royalblue;
        border-radius: 7px;
        cursor: pointer;
        border: none;
    }

    header button:hover{
        background-color: #4169e1cb;
    }

</style>