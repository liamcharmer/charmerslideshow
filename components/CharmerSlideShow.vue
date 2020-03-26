<template>
  <div class="slideshow__parent">
    <div class="slides">
      <div
        class="slide"
        v-bind:class="{'active': index == page,  'before--active': index < page , 'after--active': index > page, 'one--before--active': (page-1) == index, 'one--after--active': (page+1) == index}"
        v-bind:style="'min-height: ' + tallestHeight + 'px; width:' + 100/slidesToShow + '%'"
        v-for="(slide, index) in slides"
        v-bind:key="index"
      >
        <div class="image" v-if="slide.type == 'image'">
          <img :src="slide.content" alt />
        </div>
        <div class="text" v-if="slide.type == 'text'">
          <p>{{slide.content}}</p>
        </div>
        <div class="video" v-if="slide.type == 'video'">
          <video :src="slide.content"></video>
        </div>
      </div>
    </div>
    <div class="pagination" v-if="pagination == true">
      <!-- Automatically Generated Based on number of Slides -->
      <button
        v-for="(slide, index) in slides"
        v-on:click="changeSlide(index)"
        v-bind:key="index"
        v-bind:class="{'active': index == page, 'before--active': index < page, 'after--active': index > page, 'one--before--active': (page-1) == index, 'one--after--active': (page+1) == index}"
      >{{index+ 1}}</button>
    </div>
    <div class="arrows" v-if="arrows == true">
      <!-- Automatically Generated if there is more than one slide -->
      <button class="left" v-on:click="changeSlide(page-1)">
        <span v-if="arrowicon == true"><</span>
        <span v-else>Left</span>
      </button>
      <button class="right" v-on:click="changeSlide(page+1)">
        <span v-if="arrowicon == true">></span>
        <span v-else>Right</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    slides: {
      type: Array
      // Array must a JSON Object that contains either: "Text", "Image", "Video"
      // E.g: {type: 'text', content: 'sadjfaisdjfsdaf'} or {type: 'image', content: 'routetofile'}
    },
    arrows: {
      type: Boolean,
      default: true
    },
    pagination: {
      type: Boolean,
      default: true
    },
    arrowicon: {
      type: Boolean,
      default: true
    },
    slidesToShow: {
      type: Number,
      default: 1
    }
  },
  data: function() {
    return {
      page: 0,
      tallestHeight: 0
    };
  },
  methods: {
    changeSlide(pageToBe) {
      if (pageToBe < 0) {
        pageToBe = this.slides.length - 1;
      }
      if (pageToBe > this.slides.length - 1) {
        pageToBe = 0;
      }
      this.page = pageToBe;
    }
  },
  created() {
    console.log("asdf");
    // @TODO , make this work for changing screen size so its adaptive
    this.$nextTick(() => {
      let slideElements = document.getElementsByClassName("slide");

      for (let c = 0; c < slideElements.length; c++) {
        console.log(slideElements[c].clientHeight);
        if (slideElements[c].clientHeight > this.tallestHeight) {
          this.tallestHeight = slideElements[c].clientHeight;
        }
      }
    });
  }
};
</script>

<style lang="scss">
.slideshow__parent {
  position: relative;
  .slides {
    display: flex;
    overflow: hidden;
    position: relative;
    .slide {
      position: absolute;
      top: 0;
      left: 100%;
      width: 100%;
      transition: 0.5s all ease;
      align-items: center;
      justify-content: center;
      display: flex;
      &.active {
        position: relative;
        left: 0% !important;
      }
      &.before--active {
        left: -100%;
      }
    }
    .image {
      img {
        max-width: 100%;
      }
    }

    .text {
      font-size: 2em;
      font-weight: 700;
      text-align: center;
    }
    .video {
      video {
        max-width: 100%;
      }
    }
  }
  .pagination {
    display: flex;
    justify-content: center;
    padding: 15px;
    button {
      margin: 0 5px;
      border-radius: 100%;
      padding: 5px;
      cursor: pointer;
      border: 1px solid transparent;
      display: flex;
      width: 30px;
      outline: none;
      height: 30px;
      align-items: center;
      transition: 0.5s all ease;
      justify-content: center;
      &:hover {
        background: #efefef;
      }
      &.active {
        font-weight: 700;
        border: 1px solid black;
        &:hover {
          background: none;
        }
      }
    }
  }
  .arrows {
    display: flex;
    justify-content: center;
    padding: 15px;
    button {
      background: none;
      border: 0px;
      padding: 5px;
      margin: 0 5px;
      outline: none;
      cursor: pointer;
      &:hover {
        font-weight: 700;
      }
    }
  }
}
</style>