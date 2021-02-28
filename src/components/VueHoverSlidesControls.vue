<template>
<span class="vue-hover-slider__controls" :class="isShowControls" ref="controls">
  <span
    v-for="(image, index) in slides"
    :key="index"
    :data-key="index"
    class="vue-hover-slider__control"
    :class="{'vue-hover-slider__control--active': activeSlide === index}"
    @mouseout="activeSlide = 0"
    @mouseover="activeSlide = index">
    <span class="vue-hover-slider__control-mark"></span>
  </span>
</span>
</template>
т
<script>
export default {
  name: 'VueHoverSlidesControls',
  props: {
    slides: {
      type: Array,
      required: true
    },
    value: {
      type: Number,
      required: true
    }
  },
  computed: {
    activeSlide: {
      get () {
        return this.value
      },
      set (v) {
        this.$emit('input', v)
      }
    },
    isShowControls () {
      return {
        'hide-controls': this.slides.length <= 1
      }
    }
  },
  mounted () {
    if (!this.$refs.controls) return
    this.$refs.controls.addEventListener('touchmove', e => {
      const myLocation = e.changedTouches[0]
      const realTarget = document.elementFromPoint(myLocation.clientX, myLocation.clientY)

      const currentIndex = +realTarget?.dataset.key
      if (currentIndex || currentIndex === 0) {
        this.activeSlide = currentIndex
      }
    })
  }
}
</script>
