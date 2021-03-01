<template>
<div :style="containerStyles">
  <div class="vue-hover-slider" v-if="slides.length > 0">
    <a v-if="link" :href="link" :target="linkTarget">
      <slides-controls
        :slides="slicedSlides"
        v-model="activeSlide"
      />
    </a>
    <slides-controls
      v-else
      :slides="slicedSlides"
      v-model="activeSlide"
    />
    <div class="vue-hover-slider__images">
      <span
        v-for="(image, index) in slicedSlides"
        :key="index"
        class="vue-hover-slider__image"
        :class="{'vue-hover-slider__image--visible': activeSlide === index, 'last-slide': index === countSlides-1 && countSlides >= maxSlidesToShow}"
        :style="`background-image: url('${image}')`">
        <span v-if="countSlidesLeft" class="vue-hover-slider__image-overlay">
          <span>
            <slot name="more" :count="countSlidesLeft">
              +{{ countSlidesLeft }} {{ countSlidesLeft > 1 ? 'images' : 'image' }}
            </slot>
          </span>
        </span>
      </span>
    </div>
  </div>
  <a
    v-else-if="link"
    :href="link"
    :target="linkTarget"
    class="vue-hover-slider__image vue-hover-slider__image--visible"
    :style="`background-image: url(${defaultImage})`"></a>
  <div
    v-else
    class="vue-hover-slider__image vue-hover-slider__image--visible"
    :style="`background-image: url(${defaultImage})`"></div>
</div>
</template>

<script>
import SlidesControls from '@/components/VueHoverSlidesControls'

export default {
  name: 'VueHoverSlider',
  components: {
    SlidesControls
  },
  props: {
    slides: {
      type: Array,
      required: true
    },
    link: {
      type: String,
      required: false,
      default: ''
    },
    openInNewTab: {
      type: Boolean,
      required: false,
      default: false
    },
    maxSlidesToShow: {
      type: Number,
      required: false,
      default: Infinity
    },
    defaultImage: {
      type: String,
      required: false,
      default: require('@/assets/images/default_image.jpg')
    },
    height: {
      type: Number,
      required: false,
      default: 250
    }
  },
  data: () => ({
    activeSlide: 0,
    requiredDefaultImage: null
  }),
  computed: {
    linkTarget () {
      return this.openInNewTab ? '_blank' : '_self'
    },
    containerStyles () {
      return {
        height: this.height ? `${this.height}px` : ''
      }
    },
    slicedSlides () {
      return this.slides.slice(0, this.maxSlidesToShow)
    },
    countSlides () {
      return this.slicedSlides.length
    },
    countSlidesLeft () {
      return this.slides.length > this.countSlides ? this.slides.length - this.countSlides : 0
    }
  },
  methods: {
    preloadImages () {
      if (Array.isArray(this.slides) && this.slides.length > 0) {
        this.slides.forEach(slide => {
          const image = new Image()
          image.src = slide
        })
      }
    }
  },
  mounted () {
    this.preloadImages()
  }
}
</script>

<style lang="scss" src="@/assets/styles/index.scss"></style>
