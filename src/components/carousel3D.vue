<template>
  <!-- bind the swipe event, no matter direction -->
<span v-touch:swipe="swipeHandler">Swipe Here</span>
  <div class="container">
    <div class="carousel-container"  @mousedown="(event) => console.log(event)">
      <div
        class="carousel-3D"
        v-bind:style="{
          '-webkit-transform': 'rotateY(' + currentDegree + 'deg)',
          '-moz-transform': 'rotateY(' + currentDegree + 'deg)',
          '-o-transform': 'rotateY(' + currentDegree + 'deg)',
          transform: 'rotateY(' + currentDegree + 'deg)',
          transition: 'transform ease-in-out 1s',
        }"
      >
        <CarouselCard
          v-for="(card, index) in cardsData"
          :key="index"
          :linkText="card.linkText"
          :imgURL="card.imgURL"
          :rotationDegrees="(index * 360) / cardsData.length"
        />
      </div>
    </div>
    <div class="carousel-buttons">
      <button class="carousel-btn" v-on:click="rotate('prev')">
        &#129028;
      </button>
      <button class="carousel-btn" v-on:click="rotate('next')">
        &#129030;
      </button>
    </div>
  </div>
</template>

<script>
import CarouselCard from "./carouselCard.vue";

export default {
  name: "carousel3D",
  components: {
    CarouselCard,
  },
  props: {
    cardsData: Array,
  },
  data() {
    return {
      currentDegree: 0,
    };
  },
  methods: {
    rotate: function (direction) {
      if (direction === "prev") {
        this.currentDegree = this.currentDegree + 360 / this.cardsData.length;
        
      } else {
        this.currentDegree = this.currentDegree - 360 / this.cardsData.length;
        
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  position: relative;
}

.carousel-container {
  margin: 90px auto 150px;
  width: var(--slider-width);
  height: 200px;
  position: relative;
  cursor: grab;
  transform-style: preserve-3d;
  perspective: 1000px;
  transform: rotateX(-7deg);
}

.carousel-3D {
  height: 100%;
  width: 100%;
  position: absolute;
  transform-style: preserve-3d;
}

.carousel-buttons {
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 740px;
  margin-inline: auto;
  padding-inline: 20px;
  pointer-events: none;
}

.carousel-btn {
  background: linear-gradient(180deg, #fff 0%, #c0a3de 100%);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  pointer-events: all;
  font-weight: 700;
  font-size: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #48038f;
}
</style>
