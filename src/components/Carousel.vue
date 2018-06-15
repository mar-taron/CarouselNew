<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
import $ from 'jquery';
import '../../node_modules/slick-carousel/slick/slick.css';
import '../../node_modules/slick-carousel/slick/slick-theme.css';

// Check if the request came from the browser and is not server rendered
if (typeof window !== 'undefined') {
  const slick = require('slick-carousel')
}
export default {
  name: 'Carousel',
  props: {
    options: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  mounted() {
    this.create();
  },
  destroyed() {
    $(this.$el).slick('unslick');
  },
  methods: {
    create() {
      const $slick = $(this.$el);
      $slick.on('afterChange', this.onAfterChange);
      $slick.on('beforeChange', this.onBeforeChange);
      $slick.on('breakpoint', this.onBreakpoint);
      $slick.on('destroy', this.onDestroy);
      $slick.on('edge', this.onEdge);
      $slick.on('init', this.onInit);
      $slick.on('reInit', this.onReInit);
      $slick.on('setPosition', this.onSetPosition);
      $slick.on('swipe', this.onSwipe);
      $slick.on('lazyLoaded', this.onLazyLoaded);
      $slick.on('lazyLoadError', this.onLazyLoadError);
      $slick.slick(this.options);
    },
    destroy() {
      const $slick = $(this.$el);
      $slick.off('afterChange', this.onAfterChange);
      $slick.off('beforeChange', this.onBeforeChange);
      $slick.off('breakpoint', this.onBreakpoint);
      $slick.off('destroy', this.onDestroy);
      $slick.off('edge', this.onEdge);
      $slick.off('init', this.onInit);
      $slick.off('reInit', this.onReInit);
      $slick.off('setPosition', this.onSetPosition);
      $slick.off('swipe', this.onSwipe);
      $slick.off('lazyLoaded', this.onLazyLoaded);
      $slick.off('lazyLoadError', this.onLazyLoadError);
      $(this.$el).slick('unslick');
    },
    reSlick() {
      this.destroy();
      this.create();
    },
    next() {
      $(this.$el).slick('slickNext');
    },
    prev() {
      $(this.$el).slick('slickPrev');
    },
    pause() {
      $(this.$el).slick('slickPause');
    },
    play() {
      $(this.$el).slick('slickPlay');
    },
    goTo(index, dontAnimate) {
      $(this.$el).slick('slickGoTo', index, dontAnimate);
    },
    currentSlide() {
      return $(this.$el).slick('slickCurrentSlide');
    },
    add(element, index, addBefore) {
      $(this.$el).slick('slickAdd', element, index, addBefore);
    },
    remove(index, removeBefore) {
      $(this.$el).slick('slickRemove', index, removeBefore);
    },
    filter(filterData) {
      $(this.$el).slick('slickFilter', filterData);
    },
    unfilter() {
      $(this.$el).slick('slickUnfilter');
    },
    getOption(option) {
      $(this.$el).slick('slickGetOption', option);
    },
    setOption(option, value, refresh) {
      $(this.$el).slick('slickSetOption', option, value, refresh);
    },
    setPosition() {
      $(this.$el).slick('setPosition');
    },
    // Events
    onAfterChange(event, slick, currentSlide) {
      this.$emit('afterChange', event, slick, currentSlide);
    },
    onBeforeChange(event, slick, currentSlide, nextSlide) {
      this.$emit('beforeChange', event, slick, currentSlide, nextSlide);
    },
    onBreakpoint(event, slick, breakpoint) {
      this.$emit('breakpoint', event, slick, breakpoint);
    },
    onDestroy(event, slick) {
      this.$emit('destroy', event, slick);
    },
    onEdge(event, slick, direction) {
      this.$emit('edge', event, slick, direction);
    },
    onInit(event, slick) {
      this.$emit('init', event, slick);
    },
    onReInit(event, slick) {
      this.$emit('reInit', event, slick);
    },
    onSetPosition(event, slick) {
      this.$emit('setPosition', event, slick);
    },
    onSwipe(event, slick, direction) {
      this.$emit('swipe', event, slick, direction);
    },
    onLazyLoaded(event, slick, image, imageSource) {
      this.$emit('lazyLoaded', event, slick, image, imageSource);
    },
    onLazyLoadError(event, slick, image, imageSource) {
      this.$emit('lazyLoadError', event, slick, image, imageSource);
    },
  },
};
</script>

<style>


/* Arrows */
.slick-prev,
.slick-next
{
    z-index: 777;
    font-size: 0;
    line-height: 0;
    position: absolute;
    top: 50%;
    display: block;
    width: auto;
    height: auto;
    padding: 0;
    -webkit-transform: translate(0, -50%);
    -ms-transform: translate(0, -50%);
    transform: translate(0, -50%);
    cursor: pointer;
    color: transparent;
    border: none;
    outline: none;
    background: transparent;
}
.slick-prev:hover,
.slick-prev:focus,
.slick-next:hover,
.slick-next:focus
{
    color: transparent;
    outline: none;
    background: transparent;
}
.slick-prev:hover:before,
.slick-prev:focus:before,
.slick-next:hover:before,
.slick-next:focus:before
{
    opacity: 1;
}
.slick-prev.slick-disabled:before,
.slick-next.slick-disabled:before
{
    opacity: .25;
}

.slick-prev:before,
.slick-next:before
{
    font-family: 'slick';
    font-size: 20px;
    line-height: 1;
    opacity: .75;
    color: white;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

.slick-prev
{
    left: -25px;
}
[dir='rtl'] .slick-prev
{
    right: -25px;
    left: auto;
}
.slick-prev:before
{
    content: '←';
}
[dir='rtl'] .slick-prev:before
{
    content: '→';
}

.slick-next
{
    right: -25px;
}
[dir='rtl'] .slick-next
{
    right: auto;
    left: -25px;
}
.slick-next:before
{
    content: '→';
}
[dir='rtl'] .slick-next:before
{
    content: '←';
}

/* Dots */
.slick-dotted.slick-slider
{
    margin-bottom: 30px;
}

.slick-dots
{
    position: absolute;
    bottom: -25px;
    display: block;
    width: 100%;
    padding: 0;
    margin: 0;
    list-style: none;
    text-align: center;
}
.slick-dots li
{
    position: relative;
    display: inline-block;
    width: 20px;
    height: 20px;
    margin: 0 5px;
    padding: 0;
    cursor: pointer;
}
.slick-dots li button
{
    font-size: 0;
    line-height: 0;
    display: block;
    width: 20px;
    height: 20px;
    padding: 5px;
    cursor: pointer;
    color: transparent;
    border: 0;
    outline: none;
    background: transparent;
}
.slick-dots li button:hover,
.slick-dots li button:focus
{
    outline: none;
}
.slick-dots li button:hover:before,
.slick-dots li button:focus:before
{
    opacity: 1;
}
.slick-dots li button:before
{
    font-family: 'slick';
    font-size: 6px;
    line-height: 20px;
    position: absolute;
    top: 0;
    left: 0;
    width: 20px;
    height: 20px;
    content: '•';
    text-align: center;
    opacity: .25;
    color: black;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
.slick-dots li.slick-active button:before
{
    opacity: .75;
    color: black;
}
.slick-slide img {
  display: block;
  height: 300px;
  width: 100%;
}
.slick-prev:before, .slick-next:before{
  font-size: 40px;
}
.slick-next{
  right: 20px;
}
.slick-prev{
  left: 20px;
}

</style>
