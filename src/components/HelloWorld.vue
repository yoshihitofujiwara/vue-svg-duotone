<template>
  <div class="hello">

<svg viewBox="0 0 266 400">
  <filter id="greyscale">
   <feColorMatrix type="matrix"
      values=".33 .33 .33 0 0
              .33 .33 .33 0 0
              .33 .33 .33 0 0
              0 0 0 1 0" >
		</feColorMatrix>

    <feComponentTransfer color-interpolation-filters="sRGB">
      <feFuncR type="table" tableValues=".996078431 .984313725"></feFuncR>
      <feFuncG type="table" tableValues=".125490196 .941176471"></feFuncG>
      <feFuncB type="table" tableValues=".552941176 .478431373"></feFuncB>
    </feComponentTransfer>
	 </filter>



  <image xlink:href="../../static/assets/img/ANJ101035822.jpg" width="100%" x="0" y="0" height="100%" filter="url(#greyscale)"></image>
</svg>


  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
svg{
	width: 400px;
}
</style>
