<script>
	import { onMount } from 'svelte'
	import mapboxgl from "mapbox-gl";
	import notScarborough from "./data/notScarborough.geo.json"
	import bikeRoutes from "./data/bikeRoutes.geo.json"
	import futureTransit from "./data/futureTransit.geo.json"
	import futureTransitStations from "./data/futureTransitStations.geo.json"
	import greenwayNetwork from "./data/greenwayNetwork.geo.json"
	import Info from "./lib/Info.svelte";

	mapboxgl.accessToken = 'pk.eyJ1Ijoic2Nob29sb2ZjaXRpZXMiLCJhIjoiY2w4c3h6M2tuMDIwazNuczU3bXA3ZXpvaSJ9.ShjnM8qiYP6yqz2PcAUBOg';

	let map;

	let pageWidth;
	
	const maxBounds = [
		[-79.56371, 43.56172], // SW coords
		[-79.04763, 44.03074] // NE coords
	];

	const scarBounds = [
		[-79.30, 43.66], // SW coords
		[-79.10, 43.78] // NE coords
	]
	
	onMount(() => {

		greenwayNetwork.features = greenwayNetwork.features.filter(d => d.properties.interim === 0);

		const greenwayNetworkDash = JSON.parse(JSON.stringify(greenwayNetwork));
		
		greenwayNetworkDash.features = greenwayNetworkDash.features.filter(d => d.properties.proposed === 1);

		map = new mapboxgl.Map({
			container: 'map', 
			style: 'mapbox://styles/schoolofcities/cl8sy8euo002f14tbqhwrexda',
			center: [-79.22, 43.765], 
			zoom: 12,
			maxZoom: 13.5,
			minZoom: 8,
			bearing: -17.7,
			maxBounds: maxBounds,
			projection: 'globe',
			scrollZoom: true,
			attributionControl: false
		});
		
		map.addControl(new mapboxgl.NavigationControl(), 'top-left');

		const scale = new mapboxgl.ScaleControl({
			maxWidth: 100,
			unit: 'metric'
			});
		map.addControl(scale, 'bottom-left');

		// adding additional layers from geojson
		map.on('load', function() {

			const layers = map.getStyle().layers;

			// Find the index of the first symbol layer in the map style.
			let firstSymbolId;
			for (const layer of layers) {
				if (layer.type === 'symbol') {
					firstSymbolId = layer.id;
					break;
				}
			}

			map.addSource('notScarborough', {
				'type': 'geojson',
				'data': notScarborough.features[0]
			});

			map.addSource('bikeRoutes', {
				'type': 'geojson',
				'data': bikeRoutes
			});

			map.addSource('futureTransit', {
				'type': 'geojson',
				'data': futureTransit
			});

			map.addSource('futureTransitStations', {
				'type': 'geojson',
				'data': futureTransitStations
			});

			map.addSource('greenwayNetwork', {
				'type': 'geojson',
				'data': greenwayNetwork
			});

			map.addSource('greenwayNetworkDash', {
				'type': 'geojson',
				'data': greenwayNetworkDash
			});

			map.addLayer({
				'id': 'bike',
				'type': 'line',
				'source': 'bikeRoutes',
				'layout': {},
				'paint': {
					'line-color': '#8DBF2E', 
					'line-width': 1
				}
			}, 'rail');

			map.addLayer({
				'id': 'futureTransitStations',
				'type': 'circle',
				'source': 'futureTransitStations',
				'layout': {},
				'paint': {
					'circle-color': '#dfc8c8', 
					'circle-radius': [
						"interpolate",
						["linear"],
						["zoom"],
						8,
						2,
						16,
						10
					]
				}
			}, 'rail');

			map.addLayer({
				'id': 'futureTransit',
				'type': 'line',
				'source': 'futureTransit',
				'layout': {},
				'paint': {
					'line-color': '#dfc8c8', 
					'line-width': 2,
					'line-dasharray': [2,2]
				}
			}, 'rail');

			map.addLayer({
				'id': 'greenwayNetworkHover',
				'type': 'line',
				'source': 'greenwayNetwork',
				'layout': {},
				'paint': {
					'line-color': '#666666', 
					'line-width': 8,
					'line-opacity': 0
				}
			}, 'bridge-simple');

			map.addLayer({
				'id': 'greenwayNetwork',
				'type': 'line',
				'source': 'greenwayNetwork',
				'layout': {},
				'paint': {
					'line-color': [
						'match',
						['get', 'route'],
						'east_highland',
						'#6d9424',
						'west_highland',
						'#00A189',
						'meadoway',
						'#e6bc01',
						'taylor_massey',
						'#df1989',
						'lake_ontario',
						'#325ba8',
						// '#6FC7EA',
						'rouge_park',
						'#be4535',
						'finch',
						'#872698',
						/* other */ '#ccc'
						],
					'line-width': 4					
				}
			}, 'bridge-simple');

			map.addLayer({
				'id': 'greenwayNetworkDash',
				'type': 'line',
				'source': 'greenwayNetworkDash',
				'layout': {},
				'paint': {
					'line-color': '#fff', 
					'line-width': 4,
					'line-dasharray': [0.5,0.5]
				}
			});

			map.addLayer({
				'id': 'nsFill',
				'type': 'fill',
				'source': 'notScarborough',
				'layout': {},
				'paint': {
					'fill-color': '#fff', 
					'fill-opacity': 0.6
				}
			});

			map.addLayer({
				'id': 'nsLine',
				'type': 'line',
				'source': 'notScarborough',
				'layout': {},
				'paint': {
					'line-color': '#0D534D', 
					'line-width': 1,
					'line-dasharray': [4,1],
					'line-opacity':1
				}
			});

		});

		if (pageWidth < 500) {
		map.zoomTo(10)
		} else if (pageWidth < 700) {
		map.zoomTo(10.5)
		} else if (pageWidth < 900) {
		map.zoomTo(11)
		} else if (pageWidth < 1100) {
		map.zoomTo(11.5)
		} else {
		map.zoomTo(11.75)
		}
		
	});
	
</script>


<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin> 
	<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">

	<link href='https://api.mapbox.com/mapbox-gl-js/v2.10.0/mapbox-gl.css' rel='stylesheet' />

	<link href='./assets/style.css' rel='stylesheet' />
</svelte:head>




<main>

	<div id='map-wrapper' class="{pageWidth < 551 ? 'maps-small' : 'maps-big'}" >
		<div id="map" bind:offsetWidth={pageWidth} ></div>
	</div>

	<Info {pageWidth}/>

</main>




<style>
	
	@font-face {
		font-family: TradeGothicBold;
		src: url("./assets/Trade Gothic LT Bold.ttf");
	}
	:root {
		font-family: 'Roboto', sans-serif;
	}

	main {
		margin: auto;
		width: 100%;
		margin-bottom: -15px;
	}

	:global([data-svelte-search]) {
		border: solid 1px lightgrey;
		border-radius: 4px;
		background-color: none;
	}
	:global([data-svelte-search] li) {
		height: 50px;
	}
	:global([data-svelte-search] label) {
		display: none;
	}
	:global([data-svelte-typeahead] mark)  {
		color: #1E3765;
		background-color: #F1C500;
	}
	:global(body) {
		padding: 0px;
		margin: 0px;
		background-color: #fff;
	}

	#map-wrapper {
		margin-top: 0px;
		width: 100%;
		top: 0;
        left: 0;
		position: absolute;
		z-index: -99;
	}

	#map {
		height: 100%;
		width: 100%;
		top: 0;
        left: 0;
		position: absolute;
		z-index: -99;
	}

	.maps-big {
		height: calc(100vh - 0px);
	}

	.maps-small {
		height: calc(100vh - 342px - 0px);
	}

</style>
