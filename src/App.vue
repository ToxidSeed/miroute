<template>
 <div style="height:100vh"> 
	<l-map
		style="height: 100%"
		:zoom="zoom"
		:center="center"
	>

		<l-tile-layer :url="url"
			:id="id"
		>
		</l-tile-layer>
		<l-marker :lat-lng="plaza_libertad">
			<l-icon icon-url="./tuscany_color.png"
				:icon-size="dynamicSize"
			>
			</l-icon>
	<!--			<l-popup>
					<div @click="innerClick">
					I am a popup
					</div>
				</l-popup>
	-->
			<l-tooltip :options="{ permanent: true, interactive: true }">
				<div @click="innerClick">
					Plaza Libertad 
				</div>
			</l-tooltip>
		</l-marker>
		<l-marker :lat-lng="azampata">
                        <l-icon icon-url="./Ruin.png"
                                :icon-size="dynamicSize"
                        >
                        </l-icon>
                        <l-tooltip :options="{ permanent: true, interactive: true }">
                                <div @click="innerClick">
                                        azampata
                                </div>
                        </l-tooltip>
                </l-marker>

		<l-marker :lat-lng="quiulacocha">
                        <l-icon icon-url="./lake.png"
                                :icon-size="dynamicSize"
                        >
			</l-icon>
                        <l-tooltip :options="{ permanent: true, interactive: true }">
                                <div @click="innerClick">
					quiulacocha
                                </div>
                        </l-tooltip>
                </l-marker>
		<l-marker :lat-lng="casaracra"> 
                        <l-icon icon-url="./Ruin.png" 
                                :icon-size="dynamicSize" 
                        > 
                        </l-icon> 
                        <l-tooltip :options="{ permanent: true, interactive: true }"> 
                                <div @click="innerClick"> 
					Atacayan
                                </div> 
                        </l-tooltip> 
                </l-marker>	</l-map>
 </div>
</template>

<script>
import { latLng} from "leaflet";
import { LMap, LTileLayer,LMarker,LIcon,/*LPopup*/LTooltip } from "vue2-leaflet";

export default {
  name: "Example",
  components: {
	LMap,
	LTileLayer,
	LMarker,
	LIcon/*,
	LPopup*/,
	LTooltip
  },
  data() {
    return {
	zoom:15,
	center:   latLng(-11.516450, -75.900012),
	url: "https://api.mapbox.com/v4/mapbox.streets/{z}/{x}/{y}.png?access_token=pk.eyJ1IjoiY2hhY2hvbWlndWVsIiwiYSI6ImNqNXh5d3p1dzA5cWcyd2xoYXVibnpwdDcifQ.SL1EcjSYuczLSynh9qkPDA",
//	url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
	id:'mapbox.streets',
	plaza_libertad: latLng(-11.516450, -75.900012),
	azampata: latLng( -11.525603, -75.900040),
	quiulacocha: latLng(-10.699309, -76.279053),
	casaracra: latLng(-11.458187, -75.955077),
	iconSize:32
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
	methods:{
		innerClick(){
			console.log("meotods");
			alert("click!");
		}
	}
};
</script>

<style>
</style>
