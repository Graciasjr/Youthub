<script>

</script>

<div>

</div>

<style>
    div{
        display: inline-block;
		width: 35px;
		height: 23px;
		/* border-radius: 50px; */
		position: relative;
		background: royalblue;
    }

    div::after{
        position: absolute;
		content: "";
		bottom:22%;
		left:35%;
		width: 0;
		border:7px solid transparent ;
		border-top: 0px;
		border-bottom:12px solid #fff;
		transform: rotate(90deg);
    }
</style>