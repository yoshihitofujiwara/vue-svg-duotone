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
		<p><a href="" target="_blank">
			<SvgDuotone class="svg_duotone"
				:image="image"
				:passive="passive"
				:active="active"
				:duration="duration"
				:ease="ease"
			/>

			<!--
			<SvgDuotone class="svg_duotone"
				image="./assets/img/ANJ101035822.jpg"
				:passive="{saturate: 1}"
				:active="{saturate: 0, color: [0xe7475e, 0xf0d879]}"
				:duration="0.8"
			/>
			-->
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
