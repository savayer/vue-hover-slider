<template>
  <div class="container">
    <h1>Hover slider</h1>
    <div class="row">
      <div class="item">
        <vue-hover-slider
          :slides="slides"
          :height="350"
        />
        <p>Show all photos</p>
      </div>
      <div class="item">
        <vue-hover-slider
          :slides="slides"
          :height="350"
          :max-slides-to-show="5"
        />
        <p>Using <pre>maxSlidesToShow</pre></p>
      </div>
      <div class="item">
        <vue-hover-slider
          :slides="[]"
          :height="350"
        />
        <p>Without images</p>
      </div>
      <div class="item">
        <vue-hover-slider
          :slides="[]"
          :height="350"
          :default-image="require('@/assets/images/custom.webp')"
        />
        <p>
          Custom default image
          <pre>:default-image="require('@/assets/images/custom.webp')"</pre>
        </p>
      </div>
      <div class="item">
        <vue-hover-slider
          :slides="slides"
          :height="350"
          link="http://google.com"
          open-in-new-tab
          :max-slides-to-show="3"
        />
        <p>Set <pre>link</pre> prop</p>
      </div>
      <div class="item">
        <vue-hover-slider
          :slides="slides"
          :height="350"
          :max-slides-to-show="3"
        >
          <template #more="{ count }">
            more {{ count }} photos
          </template>
        </vue-hover-slider>
        <p>Using <pre>more</pre> slot for custom text</p>
      </div>
    </div>
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
      'https://madhunter.ru/wp-content/uploads/2019/12/opisanie-lisitsy.jpg',
      'https://cdn.fishki.net/upload/post/2018/05/04/2588849/7620afabdb00b651da45d24a6bf29de3.jpg',
      'https://wallpaperscave.ru/images/original/18/03-07/animals-foxes-26078.jpg',
      'https://wallpaperscave.ru/images/original/18/05-07/animals-foxes-49093.jpg',
      'https://s1.1zoom.ru/big3/136/Foxes_Glance_Foliage_536041_3000x2000.jpg',
      'https://kipmu.ru/wp-content/uploads/lsndrvd.jpg',
      'https://wallbox.ru/resize/1920x1200/wallpapers/main/201601/cd9dbb458e3bb66.jpg',
      'https://s1.1zoom.ru/big3/270/348443-sepik.jpg'
    ]
  })
}
</script>

<style lang="scss">
  body {
    font-family: sans-serif;
  }

  pre {
    display: inline-block;
    background: #585858;
    margin: 0;
    color: #fff;
    font-weight: bold;
    padding: 2px 3px;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
  }

  .row {
    display: flex;
    flex-wrap: wrap;
    margin-left: -.9375rem;
    margin-right: -.9375rem;
  }

  .item {
    margin-left: .9375rem;
    margin-right: .9375rem;
    width: calc(50% - 1.875rem);
    margin-bottom: 2rem;

    @media (max-width: 767px) {
      width: 100%;
    }
  }
</style>