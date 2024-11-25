<template>
  <Carousel3D :cardsData= fetchedCardsData />
</template>

<script>
import Carousel3D from "./components/carousel3D.vue";

export default {
  name: "App",
  components: {
    Carousel3D,
  },
  data() {
    return {
      fetchedCardsData: [
        { linkText: "show more", imgURL: "./assets/59d25ae975834f222e0d461af717678e.jpg" },
        { linkText: "show more" },
        { linkText: "show more" },
        { linkText: "show more" },
        { linkText: "show more" },
        { linkText: "show more" },
      ],
    };
  },
};
</script>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
}

:root {
  --num-of-cards: 6;
  --slider-width: 250px;
}

body,
h1,
h2,
h3,
h4,
p,
ul {
  margin: 0;
}

ul {
  list-style: none;
  padding-left: 0;
}

a {
  text-decoration: none;
}

button {
  cursor: pointer;
}

button,
input {
  outline: none;
}

button {
  border: none;
  background-color: #fff;
}

body {
  font-family: "poppins", system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue",
    sans-serif;
  line-height: normal;
  font-style: normal;
  width: 100%;
  height: 100%;
  min-height: 100vh;
  background: #330e66;
  background: linear-gradient(#330e66, #ebdcff, #330e66);
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
