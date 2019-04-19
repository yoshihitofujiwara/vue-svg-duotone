<template>
  <div id="app">
		<h1>vue-svg-duotone</h1>
			<SvgDuotone
				@mouseleave="onPassive"
				@mouseenter="onActive"
				@touchstart="toggle"
				ref="svg_duotone"
				:image="image"
				:passive="passive"
				:active="active"
				:duration="duration"
				:ease="ease"
			/>
			<!-- <SvgDuotone class="svg_duotone"
				image="./assets/img/img01.jpg"
				:off="{saturate: 1}"
				:active="{saturate: 0, color: [0xe7475e, 0xf0d879]}"
				:duration="0.8"
				:ease="Power2.easeInOut"
			/> -->
  </div>
</template>


<script>
import dat from "dat.gui";
import SvgDuotone from "./components/SvgDuotone.vue";

let gui;

export default {
  name: 'app',
  components: {
    SvgDuotone
  },

	data(){
		return {
			image: "./assets/img/img02.jpg",
			passive: {
				saturate: 1,
				color: [null, null]
			},
			active: {
				saturate: 0,
				// color: [null, null]
				color: [0xe7475e, 0xf0d879]
			},
			duration: 0.8,
			ease: "Power1.easeOut",
			isActive: false
		}
	},

	mounted(){
		gui = new dat.GUI({ autoPlace: false });
		gui.domElement.style.position = "fixed";
		gui.domElement.style.top = "0";
		gui.domElement.style.right = "0";
		document.body.appendChild(gui.domElement);

		let params = {
			passiveColor: false,
			passiveColor1: 0x248888,
			passiveColor2: 0xe6e6e6,
			activeColor: true,
			activeColor1: 0xe7475e,
			activeColor2: 0xf0d879,
			easeList: [
				"Power0.easeNone",
				"Power1.easeIn",
				"Power1.easeInOut",
				"Power1.easeOut",
				"Power2.easeIn",
				"Power2.easeInOut",
				"Power2.easeOut",
				"Power3.easeIn",
				"Power3.easeInOut",
				"Power3.easeOut",
				"Power4.easeIn",
				"Power4.easeInOut",
				"Power4.easeOut",
				"Back.easeIn",
				"Back.easeOut",
				"Back.easeInOut",
				"Elastic.easeIn",
				"Elastic.easeOut",
				"Elastic.easeInOut",
				"Bounce.easeIn",
				"Bounce.easeOut",
				"Bounce.easeInOut",
				"Circ.easeIn",
				"Circ.easeOut",
				"Circ.easeInOut",
				"Expo.easeIn",
				"Expo.easeOut",
				"Expo.easeInOut",
				"Sine.easeIn",
				"Sine.easeOut",
				"Sine.easeInOut",
			]
		};

		let folderOff = gui.addFolder("OFF");
		folderOff.open();
		folderOff.add(params, "passiveColor").onChange((flag)=>{
			if(flag){
				this.passive.color = [params.passiveColor1, params.passiveColor2];
			} else {
				this.passive.color = [null, null];
			}
		});
		folderOff.addColor(params, "passiveColor1").onChange((color)=>{
			if(params.passiveColor){
				this.passive.color = [color, params.passiveColor2];
			}
		});
		folderOff.addColor(params, "passiveColor2").onChange((color)=>{
			if(params.passiveColor){
				this.passive.color = [params.passiveColor1, color];
			}
		});
		folderOff.add(this.passive, "saturate", 0, 1);

		let folderON = gui.addFolder("ON");
		folderON.open();
		folderON.add(params, "activeColor").onChange((flag)=>{
			if(flag){
				this.active.color = [params.activeColor1, params.activeColor2];
			} else {
				this.active.color = [null, null];
			}
		});
		folderON.addColor(params, "activeColor1").onChange((color)=>{
			if(params.activeColor){
				this.active.color = [color, params.activeColor2];
			}
		});
		folderON.addColor(params, "activeColor2").onChange((color)=>{
			if(params.activeColor){
				this.active.color = [params.activeColor1, color];
			}
		});
		folderON.add(this.active, "saturate", 0, 1);

		gui.add(this, "duration", 0.1, 3.0);
		gui.add(this, "ease", params.easeList);
	},

	methods: {
		onActive(){
			this.$refs.svg_duotone.onActive();
		},
		onPassive(){
			this.$refs.svg_duotone.onPassive();
		},
		toggle(){
			this.isActive = !this.isActive;
			if(this.isActive){
				this.onActive();
			} else {
				this.onPassive();
			}
		}
	}
}
</script>

<style>
*{
	margin: 0;
	padding: 0;
	border: none;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
	margin-bottom: 20px;
}
svg {
  width: 640px;
  height: 360px;
  cursor: pointer;
}
@media all and (max-width: 768px){
	svg {
		width: 100vw;
		height: 56.25vw;
		/* height: 100%; */
	}
}
</style>
