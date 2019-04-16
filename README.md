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

<table style="text-align: left">
<thead>
	<tr>
		<th>name</th>
		<th>type</th>
		<th>default</th>
		<th>description</th>
	<tr/>
</thead>
<tbody>
	<tr>
		<th>image</th>
		<th>String</th>
		<th>undefined</th>
		<th><em>Required</em> image path</th>
	<tr/>
	<tr>
		<th>passive</th>
		<th>Object</th>
		<th></th>
		<th></th>
	<tr/>
	<tr>
		<th>passive.saturate</th>
		<th>Number</th>
		<th>0</th>
		<th></th>
	<tr/>
	<tr>
		<th>passive.color</th>
		<th>[color code, color code]</th>
		<th>[null, null]</th>
		<th>color code: <a href="https://gka.github.io/chroma.js/" target="_blank">chroma.js</a></th>
	<tr/>
	<tr>
		<th>active</th>
		<th>Object</th>
		<th></th>
		<th></th>
	<tr/>
	<tr>
		<th>active.saturate</th>
		<th>Number</th>
		<th>1</th>
		<th></th>
	<tr/>
	<tr>
		<th>active.color</th>
		<th>[color code, color code]</th>
		<th>[0xe7475e, 0xf0d879]</th>
		<th>color code: <a href="https://gka.github.io/chroma.js/" target="_blank">chroma.js</a></th>
	<tr/>
	<tr>
		<th>duration</th>
		<th>Number</th>
		<th>0.8</th>
		<th>Animation Sec</th>
	<tr/>
	<tr>
		<th>ease</th>
		<th>String, Object</th>
		<th>Power2.easeOut</th>
		<th>Animation Easing: <a href="https://greensock.com/docs/Easing" target="_blank">GreenSock Ease</a></th>
	<tr/>
</tbody>
</table>


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
