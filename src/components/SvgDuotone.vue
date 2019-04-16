/*==========================================================================
	template
==========================================================================*/
<template>
  <svg @mouseenter="onActive" @mouseleave="onPassive">
    <filter id="duotone">
      <feColorMatrix type="saturate" :values="saturate"></feColorMatrix>
      <feComponentTransfer color-interpolation-filters="sRGB">
        <feFuncR type="table" :tableValues="color.r()"></feFuncR>
        <feFuncG type="table" :tableValues="color.g()"></feFuncG>
        <feFuncB type="table" :tableValues="color.b()"></feFuncB>
      </feComponentTransfer>
    </filter>
    <image :xlink:href="image" width="100%" height="100%" x="0" y="0" filter="url(#duotone)"></image>
  </svg>
</template>



/*==========================================================================
	script
==========================================================================*/
<script>
import chroma from "chroma-js"; // see: https://gka.github.io/chroma.js/
import { TweenLite } from "gsap/TweenMax";
import * as utils from "../assets/js/utils.js";

export default {
  name: "SvgDuotone",

  props: {
    image: String,

    passive: {
      type: Object,
      default: () => {
        return {
          saturate: 1,
          color: [null, null]
        };
      }
    },
    active: {
      type: Object,
      default: () => {
        return {
					saturate: 0,
					color: [0xe7475e, 0xf0d879]
          // color: [null, null]
        };
      }
    },
		duration: {
			type: Number,
      default: () => 0.8
		},
		ease: {
			type: [String, Object],
      default: () => "Power2.easeOut"
		}
  },

  /**
   * @data
   */
  data() {
    return {
      // @private
      progress: 0,
      passiveColor: {
        r: [0, 1],
        g: [0, 1],
        b: [0, 1]
      },
      activeColor: {
        r: [0, 1],
        g: [0, 1],
        b: [0, 1]
      }
    };
  },


  /**
   * @watch
   */
	watch: {
		"passive.color"() {
			this._$updateColor();
		},
		"active.color"() {
			this._$updateColor();
		}
	},


  /**
   * @computed
   */
  computed: {
    saturate() {
      return utils.lerp(this.progress, this.passive.saturate, this.active.saturate);
    },

    color() {
      return {
        r: () =>
          utils.lerp(this.progress, this.passiveColor.r[0], this.activeColor.r[0]) +
          " " +
          utils.lerp(this.progress, this.passiveColor.r[1], this.activeColor.r[1]),
        g: () =>
          utils.lerp(this.progress, this.passiveColor.g[0], this.activeColor.g[0]) +
          " " +
          utils.lerp(this.progress, this.passiveColor.g[1], this.activeColor.g[1]),
        b: () =>
          utils.lerp(this.progress, this.passiveColor.b[0], this.activeColor.b[0]) +
          " " +
          utils.lerp(this.progress, this.passiveColor.b[1], this.activeColor.b[1])
      };
    }
  },

  /**
   * @created
   */
  created() {
    this._$updateColor();
  },

  /**
   * @methods
   */
  methods: {
		onPassive(){
      TweenLite.to(this, this.duration, {
        progress: 0,
        ease: this.ease
      });
		},

		onActive(){
      TweenLite.to(this, this.duration, {
        progress: 1,
        ease: this.ease
      });
		},

    _$updateColor() {
      this.passiveColor = this._$getRGB(this.passive.color);
      this.activeColor = this._$getRGB(this.active.color);
    },

    _$getRGB(colors) {
      let rgb = {
        r: [0, 1],
        g: [0, 1],
        b: [0, 1]
      };

      if (colors && colors[0] && colors[1]) {
        let color1 = chroma(colors[0]).rgb(),
          color2 = chroma(colors[1]).rgb();
        rgb.r = [color1[0] / 255, color2[0] / 255];
        rgb.g = [color1[1] / 255, color2[1] / 255];
        rgb.b = [color1[2] / 255, color2[2] / 255];
      }
      return rgb;
    }
  }
};
</script>


/*==========================================================================
	style
==========================================================================*/
<style scoped>
/*
svg {
	width: 576px;
  height: 384px;
}
*/
</style>
