<template>
  <div class="w-full">
    <img src="/navigation1_1.png">
    <h1 class="w-full my-8 title">Wie ist deine Stimmung heute? </h1>
    <input type="range" min="0" max="4" class="w-full mb-8" v-bind:class="{slidersad: sliderState < 2, slidernormal: sliderState == 2, sliderhappy: sliderState > 2}" v-model="inputValue" id="myRange">
  </div>
</template>
<script>
  import ButtonDesign from '~/components/SelectionButton.vue';
  import WeiterButton from "../WeiterButton";

  export default {
    data() {
      return {
        sliderState: 2
      }
    },
    components: {WeiterButton, ButtonDesign},
    props: ["inputValue"],
    watch: {
      inputValue: function (val) {
        this.$emit("data", val);
        this.sliderState = val;
      }
    }
  }
</script>
<style>

  img {
    display: block;
    margin: auto;
  }

  .slidersad {
    -webkit-appearance: none;
    appearance: none;
    outline: none;
    height: 5px;
    background: white;
    border-radius: 5px;
  }

  .slidersad::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 100px; /* Set a specific slider handle width */
    height: 100px; /* Slider handle height */
    background-image: url("/mood_sad.png");
    background-size: 100px 100px;
    cursor: pointer; /* Cursor on hover */
    border-radius: 50px;
  }

  .slidernormal {
    -webkit-appearance: none;
    appearance: none;
    outline: none;
    height: 5px;
    background: white;
    border-radius: 5px;
  }

  .slidernormal::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 100px; /* Set a specific slider handle width */
    height: 100px; /* Slider handle height */
    background-image: url("/mood_neutral.png");
    background-size: 100px 100px;
    cursor: pointer; /* Cursor on hover */
    border-radius: 50px;
  }

  .sliderhappy {
    -webkit-appearance: none;
    appearance: none;
    outline: none;
    height: 5px;
    background: white;
    border-radius: 5px;
  }

  .sliderhappy::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 100px; /* Set a specific slider handle width */
    height: 100px; /* Slider handle height */
    background-image: url("/mood_happy.png");
    background-size: 100px 100px;
    cursor: pointer; /* Cursor on hover */
    border-radius: 50px;
  }
</style>
