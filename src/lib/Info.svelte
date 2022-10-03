<script>

    export let pageWidth;

</script>



<div id="panel" class="{pageWidth < 641 ? 'mobile' : 'web'}">

	<div id="title">
		<h1>Scarborough Greenway Network</h1>
		<h2>Towards the world's best offroad trail network</h2>
	</div>

	<!-- <a href="https://github.com/schoolofcities/population-change-canadian-cities-1996-2021/">
		<div id="more-less" >
			<p>click here to read more</p>
		</div>
	</a> -->

	<p id="attribution">
		Map built by <a href="https://jamaps.github.io">Jeff Allen</a> with  
		©<a href='https://www.mapbox.com/about/maps/'>Mapbox</a> & ©<a href='http://www.openstreetmap.org/copyright'>OpenStreetMap</a> / <a href='https://www.mapbox.com/map-feedback/' target='_blank'>Improve this map</a>
	</p>

</div>


<style>
    #panel {
		margin: auto;
        height: 256px;
		border-top: solid 1px #0D534D;
		float: right;
		z-index: 9;
		background-color: rgb(250, 250, 250);
        right: 0;
		position: absolute;
		opacity: 0.9;
		box-shadow: 0 3px 0 0 rgba(197, 197, 197, 0.168);
		
	}
    .mobile {
        width: 100%;
        border-top-right-radius: 0px;
        border-right: none;
		bottom: 0px;
    }
    .web {
        width: 400px;
        height: 255px;
		border-left: solid 1px #0D534D;
		border-bottom: solid 1px #0D534D;
		bottom: 25px;
    }

	#title {
		max-width: 550px;
		margin-left: 12px;
		margin-right: 12px;
		padding-bottom: 8px;
		margin-bottom: 0px;
	}

	#title h1 {
		font-family: Roboto, sans-serif;
		font-size: 21px;
		color: #0D534D
	}

	#title h2 {
		margin-top: -5px;
		color: rgb(70, 70, 70);
		font-family: Roboto, sans-serif;
		font-size: 15px;
		line-height: 1.75;
	}

	#attribution {
		font-family: Roboto, sans-serif;
		font-size: 10px;
		margin-left: 12px;
		margin-right: 12px;
	}
	#attribution a {
		color: rgb(74, 74, 74);
		text-decoration: underline;
	}
	#attribution a:hover {
		color: black;
	}

	#bold {
		color: black;
		font-weight: bold;
		font-size: 14px;
	}

	#more-less {
		height: 20px;
		margin: 0px;
		padding: 0px;
		padding-bottom: -5px;		
		margin-top: -15px;
		padding-left: 20px;
		padding-right: 20px;
		border-top: solid 1px #0D534D;
        border-bottom: solid 1px #0D534D;
		font-family: Roboto, sans-serif;
		font-size: 12px;
		background-color: rgb(225, 225, 225);
		text-align: center;
	}
	#more-less:hover {
		cursor: pointer;
		background-color: #F1C500;
	}

	#more-less p {
		color: #0D534D;
		font-family: Roboto, sans-serif;
		padding: 0px;
		margin: 0px;
	}
	
	a {
		text-decoration: none;
	}

</style>