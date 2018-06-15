<template>
  <div>
    <h1>Home</h1>
    <Carousel
      ref="slick"
      :options="slickOptions"
      @afterChange="handleAfterChange"
      @beforeChange="handleBeforeChange"
      @breakpoint="handleBreakpoint"
      @destroy="handleDestroy"
      @edge="handleEdge"
      @init="handleInit"
      @reInit="handleReInit"
      @setPosition="handleSetPosition"
      @swipe="handleSwipe">
      <div v-for="image in images" v-bind:key="image.name">
        <img class="img-fluid" :src='image.src' :alt="image.name">
      </div>
    </Carousel>
  </div>
</template>

<script>
import Carousel from './Carousel';
import image1 from '../assets/images/1.jpg'
import image2 from '../assets/images/2.jpg'
import image3 from '../assets/images/3.jpg'
import image4 from '../assets/images/4.jpg'
import image5 from '../assets/images/5.jpg'
import image6 from '../assets/images/6.jpg'
import image7 from '../assets/images/7.jpg'

export default {
  name: 'Home' ,
  components: { Carousel },
  data() {
        return {
            images: [
              {
                name: "1",
                src: image1
              },
              {
                name: "2",
                src: image2
              },
              {
                name: "3",
                src: image3
              },
              {
                name: "4",
                src: image4
              },
              {
                name: "5",
                src: image5
              },
              {
                name: "6",
                src: image6
              },
              {
                name: "7",
                src: image7
              }
            ],
            slickOptions: {
                dots: true,
                infinite: false,
                speed: 300,
                slidesToShow: 3,
                slidesToScroll: 3,
                responsive: [
                  {
                    breakpoint: 1024,
                    settings: {
                      slidesToShow: 3,
                      slidesToScroll: 3,
                      infinite: true,
                      dots: true
                    }
                  },
                  {
                    breakpoint: 600,
                    settings: {
                      slidesToShow: 2,
                      slidesToScroll: 2
                    }
                  },
                  {
                    breakpoint: 480,
                    settings: {
                      slidesToShow: 1,
                      slidesToScroll: 1
                    }
                  }
                ]
            },
        };
    },

    methods: {
        next() {
            this.$refs.slick.next();
        },

        prev() {
            this.$refs.slick.prev();
        },

        reInit() {
            this.$nextTick(() => {
                this.$refs.slick.reSlick();
            });
        },

        // Events listeners
        handleAfterChange(event, slick, currentSlide) {
            console.log('handleAfterChange', event, slick, currentSlide);
        },
        handleBeforeChange(event, slick, currentSlide, nextSlide) {
            console.log('handleBeforeChange', event, slick, currentSlide, nextSlide);
        },
        handleBreakpoint(event, slick, breakpoint) {
            console.log('handleBreakpoint', event, slick, breakpoint);
        },
        handleDestroy(event, slick) {
            console.log('handleDestroy', event, slick);
        },
        handleEdge(event, slick, direction) {
            console.log('handleEdge', event, slick, direction);
        },
        handleInit(event, slick) {
            console.log('handleInit', event, slick);
        },
        handleReInit(event, slick) {
            console.log('handleReInit', event, slick);
        },
        handleSetPosition(event, slick) {
            console.log('handleSetPosition', event, slick);
        },
        handleSwipe(event, slick, direction) {
            console.log('handleSwipe', event, slick, direction);
        }
    },
}
</script>
