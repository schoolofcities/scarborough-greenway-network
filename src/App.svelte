<script>
	import { onMount } from 'svelte'
	import mapboxgl from "mapbox-gl";
	import Top from "./lib/Top.svelte"
	import notScarborough from "./data/not_scarborough_osm.geo.json"

	import Typeahead from "svelte-typeahead";
	import Places from "./assets/places.geo.json";
	import Info from "./lib/Info.svelte";
	import Select from "./lib/Select.svelte"

	

	mapboxgl.accessToken = 'pk.eyJ1Ijoic2Nob29sb2ZjaXRpZXMiLCJhIjoiY2w4c3h6M2tuMDIwazNuczU3bXA3ZXpvaSJ9.ShjnM8qiYP6yqz2PcAUBOg';

	console.log(notScarborough.features[0])

	let map;

	let pageWidth;
	
	const bounds = [
		[-79.56371,43.56172], // Southwest coordinates
		[-79.04763, 44.03074] // Northeast coordinates
	];
	
	onMount(() => {
		map = new mapboxgl.Map({
			container: 'map', 
			style: 'mapbox://styles/schoolofcities/cl8sy8euo002f14tbqhwrexda',
			center: [-79.22, 43.765], 
			zoom: 12,
			maxZoom: 17,
			minZoom: 8,
			bearing: -17,
			maxBounds: bounds,
			projection: 'globe',
			scrollZoom: true,
			attributionControl: false
		});
		
		
		map.addControl(new mapboxgl.AttributionControl({
			customAttribution: 'Map by <a href="http://jamaps.github.io/about.html">Jeff Allen</a>'
		}), 'bottom-right');
		map.addControl(new mapboxgl.NavigationControl(), 'top-left');

		const scale = new mapboxgl.ScaleControl({
			maxWidth: 100,
			unit: 'metric'
			});
		map.addControl(scale, 'bottom-right');

		map.on('load', function() {
			map.addSource('notScarborough', {
			'type': 'geojson',
			'data': notScarborough.features[0]
		});

			map.addLayer({
				'id': 'nsFill',
				'type': 'fill',
				'source': 'notScarborough', // reference the data source
				'layout': {},
				'paint': {
					'fill-color': '#fff', // blue color fill
					'fill-opacity': 0.6
				}
			});

			map.addLayer({
				'id': 'nsLine',
				'type': 'line',
				'source': 'notScarborough', // reference the data source
				'layout': {},
				'paint': {
					'line-color': '#1E3765', // blue color fill
					'line-width': 2,
					'line-dasharray': [3,3],
					'line-opacity':0.9
				}
			});
		});

		

		// map.on('mouseenter', 'ct_fill', () => {
		// 	map.getCanvas().style.cursor = 'pointer';
		// });
		// map.on('mouseleave', 'ct_fill', () => {
		// 	map.getCanvas().style.cursor = '';
		// })

		// map.on('click', 'ct_fill', (e) => {		

		// 	var features = map.queryRenderedFeatures(e.point, { layers: ['ct_fill'] });

		// 	if (ctuid != features[0].properties.CTUID) {
		// 		var style = [
		// 			"match",
		// 			["get", "CTUID"],
		// 			[features[0].properties.CTUID],
		// 			"#f1c500",
		// 			"#fff"
		// 		]
		// 		map.setPaintProperty('ct_fill', 'fill-color', style)
		// 		ctuid = features[0].properties.CTUID

		// 	} else {
		// 		map.setPaintProperty('ct_fill', 'fill-color', '#fff')
		// 		ctuid = '0'
		// 	}

		// });

	});

	

	function placeClick(city) {
		ctuid = "0";
		map.setPaintProperty('ct_fill', 'fill-color', '#fff');
		map.panTo(city.original.geometry.coordinates);
		map.zoonTo(10);
	}


</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin> 
	<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">

	<link href='https://api.mapbox.com/mapbox-gl-js/v2.10.0/mapbox-gl.css' rel='stylesheet' />
</svelte:head>




<main>

	<Top/>

	<div id='map-wrapper' class="{pageWidth < 755 ? 'maps-small' : 'maps-big'}" >
		<!-- class="{pageWidth < 755 ? 'maps-small' : 'maps-big'}" -->
	<div id="map" bind:offsetWidth={pageWidth} ></div>

	</div>

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
		/* height: 50px; */
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
	#search-results {
		color: #1E3765;
		font-family: Roboto, sans-serif;
	}
	#search {
		position: absolute;
		width: 260px;
		top: 62px;
		left: 5px;
		z-index: 99;
		opacity: 0.93;
	}

	#map-wrapper {
		margin-top: 50px;
		/*  height: calc(100vh - 50px); */
		width: 100%;
		top: 0;
        left: 0;
		position: absolute;
		z-index: -99;
	}

	#map {
		/* margin-top: 50px; */
		height: 100%;
		width: 100%;
		top: 0;
        left: 0;
		position: absolute;
		z-index: -99;
	}

	.maps-big {
		height: calc(100vh - 50px);
	}

	.maps-small {
		height: calc(100vh - 255px - 50px);
	}

	
	
</style>
