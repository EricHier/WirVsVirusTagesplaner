<template>
  <div class="w-full">
    <h1 class="w-full my-8 title">Wie geht's dir? </h1>

    <input type="range" min="0" max="4" value="2" class="w-full slider mb-8" v-model="inputValue" id="myRange">
  </div>
</template>
<script>
  import ButtonDesign from '~/components/SelectionButton.vue';
  import WeiterButton from "../WeiterButton";

  export default {
    components: {WeiterButton, ButtonDesign},
    props: ["inputValue"],
    methods: {
      sendResult() {
        this.$emit("submit", parseInt(this.inputValue));
      },
      click() {
        this.sendResult();
      }
    }
  }
</script>
<style>
  .slider {
    appearance: none;
    outline: none;
    height: 5px;
    background: white;
    border-radius: 5px;
  }

  .slider::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 25px; /* Set a specific slider handle width */
    height: 25px; /* Slider handle height */
    background-image: url("/mood-icons/Mood_Happy.svg");
    cursor: pointer; /* Cursor on hover */
    border-radius: 50px;
  }
</style>
