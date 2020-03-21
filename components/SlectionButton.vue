<template>
  <button v-on:click="sendclick" class="custombutton outline-none">
    <slot/>
  </button>
</template>
<script>
  export default  {
    methods: {
      sendclick() {
        this.$emit("click");
      }
    }
  }
</script>
<style>
  .custombutton {
    width: 260px;
    height: 55px;
    background-color: #FFB115;
    font-size: 18px;
    font-weight: 400;
    color: white;
    border-radius: 8px;
    outline: none;
  }
</style>
