<template>
  <div class="p-4 container">
    <h1 class="w-full text-bold text-left	my-8 text-4xl">Wie geht's dir? </h1>

    <input type="range" min="0" max="5" value="2" class="w-full slider mb-8" id="myRange">

  </div>
</template>
<script>
  export default {
    methods: {
      sendResult(props) {
        this.$emit("submit", props);
      },
      sendResult0(props) {
        this.sendResult(0);
      },
      sendResult1(props) {
        this.sendResult(1);
      }
    }
  }
</script>
<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .slider {
    appearance: none;
    outline: none;
    height: 10px;
    background: #d3d3d3;
    border-radius: 5px;
  }

  .slider::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 25px; /* Set a specific slider handle width */
    height: 25px; /* Slider handle height */
    background: #4CAF50; /* Green background */
    cursor: pointer; /* Cursor on hover */
    border-radius: 5px;
  }
</style>
