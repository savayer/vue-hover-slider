<template>
  <div id="app">
    <vue-hover-slider :slides="slides" />
  </div>
</template>

<script>
import VueHoverSlider from "@/components/VueHoverSlider";

export default {
  name: 'App',
  components: {
    VueHoverSlider
  },
  data: () => ({
    slides: [
      'https://www.welcomewildlife.com/wp-content/uploads/2019/01/Red-fox-300-0-%C2%A9-Stanislav-Duben-Shutterstock-e1563829913951.jpg',
      'https://ewscripps.brightspotcdn.com/dims4/default/c5f5848/2147483647/strip/true/crop/2450x1286+0+216/resize/1200x630!/quality/90/?url=https%3A%2F%2Fmediaassets.wtkr.com%2Ftribune-network%2Ftribwtkr-files-wordpress%2F2018%2F07%2Fgettyimages-516318760.jpg'
    ]
  })
}
</script>
