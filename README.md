# vue-hover-slider

[View demo](https://savayer.github.io/vue-hover-slider/)

## Install
```
npm i -S vue-hover-slider
```

## Usage
```javascript
import VueHoverSlider from 'vue-hover-slider'
Vue.use(VueHoverSlider)
```

```html
<template>
  <vue-hover-slider :slides="slides" />
</template>

<script>
  export default {
    data: () => ({
      slides: [
        '/path/to/img'
      ]
    })
  }
</script>
```

## Props

Prop | Type | Default | Description
--------- | ---- | ------- | -----------
slides (*required*) | `Array` | - | array of images
link | `String` | `''` | link on the slides
openInNewTab | `Boolean` | `false` | target _blank or _self if `link` was set
maxSlidesToShow | `Number` | `Infinity` | max count slides to show
defaultImage | `String` | `image url` | default image if slides are empty
height | `Number` | `250` | height of the slider

## Slots

#### more

Scoped: `count`  
Usage:
```html
<vue-hover-slider
  :slides="slides"
  :height="350"
  :max-slides-to-show="3">
  <template #more="{ count }">
    more {{ count }} photos
  </template>
</vue-hover-slider>
```

## License
[The MIT License](http://opensource.org/licenses/MIT)

### Vue CLI configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
