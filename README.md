# vue-svg-duotone

<ul>
	<li><a href="http://yoshihitofujiwara.github.io/vue-svg-duotone/index.html" target="_blank">DEMO</a></li>
</ul>


___
## Usage

```
<template>
  <div id="app">
		<h1>vue-svg-duotone</h1>
		<p><a
			href="https://github.com/yoshihitofujiwara/vue-svg-duotone" target="_blank">
			<SvgDuotone class="svg_duotone"
				@mouseleave="onPassive"
				@mouseenter="onActive"
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
		</a></p>
  </div>
</template>


<script>
import SvgDuotone from "./components/SvgDuotone.vue";

export default {
  name: "app",
  components: {
    SvgDuotone
  },

	data(){
		return {
			image: "./assets/img/ANJ101035822.jpg",
			passive: {
				saturate: 1,
				color: [null, null]
			},
			active: {
				saturate: 0,
				color: [0xe7475e, 0xf0d879]
			},
			duration: 0.8,
			ease: "Power1.easeOut"
		}
	},

	methods: {
		onActive(){
			this.$refs.svg_duotone.onActive();
		},
		onPassive(){
			this.$refs.svg_duotone.onPassive();
		}
	}
}
</script>


<style>
.svg_duotone{
	width: 576px;
  height: 384px;
  cursor: pointer;
}
</style>
```

___
## Options

|name|type|default|description|
|----|----|----|----|
|image|String|undefined|<strong style="color:#f09">Required</strong> image path|
|passive|Object| | |
|passive.saturate|Number|0| |
|passive.color|[color code, color code]|[null, null]|color code: <a href="https://gka.github.io/chroma.js/" target="_blank">chroma.js</a>|
|active|Object| | |
|active.saturate|Number|1| |
|active.color|[color code, color code]|[0xe7475e, 0xf0d879]|color code: <a href="https://gka.github.io/chroma.js/" target="_blank">chroma.js</a>|
|duration|Number|0.8|Animation Duration (Sec)|
|ease|String, Object|Power2.easeOut|Animation Easing: <a href="https://greensock.com/docs/Easing" target="_blank">GreenSock Ease</a>|
|mouseenter|event| | emit mouseenter |
|mouseleave|event| | emit mouseleave |
___


## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn run serve
```

### Compiles and minifies for production
```
yarn run build
```

### Run your tests
```
yarn run test
```

### Lints and fixes files
```
yarn run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
