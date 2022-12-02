<template>
 <div style="height:100vh" id="map"> 
	
 </div>
</template>

<script>
import mapboxgl from 'mapbox-gl'; 
import 'mapbox-gl/dist/mapbox-gl.css';

export default {
  name: "Example",
  components: {

  },
  data() {
    return {
		map:{}
	/*zoom:15,
	center:   latLng(-11.516450, -75.900012),	
	id:'mapbox.streets',
	plaza_libertad: latLng(-11.516450, -75.900012),
	azampata: latLng( -11.525603, -75.900040),
	quiulacocha: latLng(-10.699309, -76.279053),
	casaracra: latLng(-11.458187, -75.955077),
	iconSize:32*/
    }
},
  computed: {
    dynamicSize () {
	console.log(this.iconSize)
	return [this.iconSize,this.iconSize*1.15];
    },
    dynamicAnchor () {
      return [this.iconSize / 2, this.iconSize * 1.15];
    }
  },
  mounted:function(){
	this.crear_mapa()
	this.add_marker()
  },
	methods:{
		crear_mapa:function(){
			mapboxgl.accessToken = 'pk.eyJ1IjoiY2hhY2hvbWlndWVsIiwiYSI6ImNqNXh5d3p1dzA5cWcyd2xoYXVibnpwdDcifQ.SL1EcjSYuczLSynh9qkPDA';
			this.map = new mapboxgl.Map({
			container: 'map', // container ID
			style: 'mapbox://styles/mapbox/streets-v12', // style URL
			center: [-77.04221094667754,-12.040683822019647], // starting position [lng, lat]			
			zoom: 9, // starting zoom
			});
			//console.log(map)
		},
		add_marker:function(){
			new mapboxgl.Marker()
			.setLngLat([-77.04221094667754,-12.040683822019647])
			.addTo(this.map);
		}
	}
};
</script>

<style>
</style>
