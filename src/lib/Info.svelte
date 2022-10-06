<script>

	import logo from '../assets/top-logo.svg'
	import sumoLogo from '../assets/sumo-logo.svg'

    export let pageWidth;

</script>



<div id="panel" class="{pageWidth < 551 ? 'mobile' : 'web'}">

	<div id="title">
		<p id="h1">The Scarborough Greenway Network</p>
		<p id="h2"><i>Building an outstanding
			offroad trail network</i></p>
	</div>

	<div id="items">

		<div id="items-status">

			<p id="item">
				

				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#464646;stroke-width:3" />
					<line x1="2" y1="5" x2="3" y2="5" style="stroke:#fff;stroke-width:3" />
					<line x1="6" y1="5" x2="7" y2="5" style="stroke:#fff;stroke-width:3" />
					<line x1="10" y1="5" x2="11" y2="5" style="stroke:#fff;stroke-width:3" />
					<line x1="14" y1="5" x2="15" y2="5" style="stroke:#fff;stroke-width:3" />
					<line x1="18" y1="5" x2="19" y2="5" style="stroke:#fff;stroke-width:3" />
				</svg>
				Proposed Trail &nbsp;

				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#464646;stroke-width:3" />
				</svg>
				Existing Trail (may need upgrades)
			</p>
		</div>

		<div id="items-left" class="{pageWidth < 395 ? 'mobile-l' : 'web-l'}">
			<p id="item">

				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#6D247A;stroke-width:3" />
				</svg>
				<a href="https://www.utsc.utoronto.ca/suburban-mobilities" target="_blank">East Highland Creek Greenway</a>
			</p>
			<p id="item">
				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#AB1368;stroke-width:3" />
				</svg>
				<a href="https://www.utsc.utoronto.ca/suburban-mobilities" target="_blank">West Highland Creek Greenway</a>
			</p>
			<p id="item">
				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#007FA3;stroke-width:3" />
				</svg>
				<a href="https://www.utsc.utoronto.ca/suburban-mobilities" target="_blank">Taylor Massey Creek Greenway</a>
			</p>
			<p id="item">
				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#00A189;stroke-width:3" />
				</svg>
				<a href="https://www.utsc.utoronto.ca/suburban-mobilities" target="_blank">Finch Hydro Corridor Greenway</a>
			</p>
		</div>

		<div id="items-right" class="{pageWidth < 395 ? 'mobile-r' : 'web-r'}">
			<p id="item">
				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#DC4633;stroke-width:3" />
				</svg>
				<a href="https://www.utsc.utoronto.ca/suburban-mobilities" target="_blank">Waterfront Greenway</a>
			</p>
			<p id="item">
				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#6FC7EA;stroke-width:3" />
				</svg>
				<a href="https://www.utsc.utoronto.ca/suburban-mobilities" target="_blank">Rouge Park Greenway</a>
			</p>
			<p id="item">
				<svg height="10" width="20">
					<line x1="0" y1="5" x2="20" y2="5" style="stroke:#F1C500;stroke-width:3" />
				</svg>
				The Meadoway
			</p>
		</div>
		
	</div>

	<div id="report">
		<p><a href="https://www.mobilitynetwork.utoronto.ca/wp-content/uploads/2022/10/The-Scarborough-Greenway-Network-Oct-2022.pdf" target="_blank">Click here to read the report  </a> by André Sorensen,
			Amaan Jabbar,
			Karen Khan,
			Allison Oki, and
			Anastasiia Ostrovskaia </p>
	</div>

	<div id="logo">
		
		<a href="https://www.schoolofcities.utoronto.ca/"><img height="55" src={logo} alt="School of Cities"></a>

		<a href="https://www.utsc.utoronto.ca/suburban-mobilities/"><img img height="65" src={sumoLogo} alt="Suburban Mobilities Research Cluster"></a>
		
	</div>

	<p id="attribution">
		Map built by <a href="https://jamaps.github.io" target="_blank">Jeff Allen</a> with  
		©<a href='https://www.mapbox.com/about/maps/' target="_blank">Mapbox</a> & ©<a href='http://www.openstreetmap.org/copyright' target="_blank">OpenStreetMap</a> / <a href='https://www.mapbox.com/map-feedback/' target='_blank'>Improve this map</a>
	</p>

</div>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin> 
	<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
</svelte:head>



<style>
    #panel {
		margin: auto;
        height: 342px;
		border-top: solid 1px #0D534D;
		float: right;
		z-index: 9;
		background-color: rgb(250, 250, 250);
        right: 0;
		position: absolute;
		opacity: 0.94;
		box-shadow: 0 3px 0 0 rgba(197, 197, 197, 0.168);
	}
    .mobile {
        width: 100%;
        border-top-right-radius: 0px;
        border-right: none;
		border-bottom: none;
		bottom: 0px;
    }
    .web {
        width: 399px;
        height: 265px;
		border-left: solid 1px #0D534D;
		border-bottom: solid 1px #0D534D;
		bottom: 5px;
	}
	#title {
		margin-left: 12px;
		margin-right: 12px;
		margin-bottom: 0px;
		border-bottom: solid 1px #0D534D;
	}
	#h1 {
		font-family: 'Roboto';
		font-style: normal;
		font-weight: 700;
		font-size: 22px;
		color: #0D534D;
		padding: 0px;
		padding-top: 12px;
		padding-bottom: 0px;
		margin: 0px;
		line-height: 25vpx;
	}
	#h2 {
		margin-top: -5px;
		color: rgb(70, 70, 70);
		font-family: Roboto, sans-serif;
		font-size: 16px;
		line-height: 1.75;
		padding: 0px;
		padding-top: 5px;
		padding-bottom: 5px;
		margin: 0px;
		line-height: 25px;
	}

	#items {
		margin-left: 12px;
		margin-right: 12px;
		padding-top: 8px;
		padding-bottom: 8px;
		border-bottom: solid 1px #0D534D;
		overflow: hidden;
	}
	#items-status {
		padding-bottom: 7px;
	}
	#items-left {
		padding-right: 15px;
	}
	/* #items-right {
		margin-left: 15px;
	} */
	.web-l {
		float: left;
	}
	.mobile-l {
		float: none;
	}
	.web-r {
		margin-left: 15px;
	}
	.mobile-r {
		margin-left: 0px;
	}
	#item {
		font-family: Roboto, sans-serif;
		font-size: 13px;
		margin: 0px;
		padding: 0px;
		color: #464646;
		line-height: 16px;
	}
	#item a {
		color: #007FA3;
		text-decoration: underline;
	}
	#item a:hover {
		color: #1E3765;
	}

	#report {
		font-family: Roboto, sans-serif;
		font-size: 13px;
		padding-top: 8px;
		margin-top: 0px;
		padding-bottom: 8px;
		margin-left: 12px;
		margin-right: 12px;
		border-bottom: solid 1px #0D534D;
		line-height: 16px;
	}
	#report p {
		padding: 0px;
		margin: 0px;
		color: rgb(70, 70, 70);
	}
	#report a {
		color: #007FA3;
		text-decoration: underline;
	}
	#report a:hover {
		color: #1E3765;
	}

	#logo {
		padding-top: 5px;
		margin-left: 12px;
		margin-right: 12px;
		border-bottom: solid 1px #0D534D;
	}
	#logo a:hover {
		opacity: 0.7;
	}

	#attribution {
		font-family: Roboto, sans-serif;
		font-size: 10px;
		margin-left: 12px;
		margin-right: 12px;
		line-height: 15px;
	}
	#attribution a {
		color: #007FA3;
		text-decoration: underline;
	}
	#attribution a:hover {
		color: #1E3765;
	}

</style>
