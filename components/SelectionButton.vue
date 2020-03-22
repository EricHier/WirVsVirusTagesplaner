<template>
  <button v-on:click="sendclick" class="selected outline-none nunito" v-bind:class="{'custombutton' : selected}">
    <slot/>
  </button>
</template>
<script>
  export default  {
    props: ["selected"],
    methods: {
      sendclick() {
        this.$emit("click");
      }
    }
  }
</script>
<style>
  .custombutton {
    background-color: #FFB115 !important;
    font-weight: 400 !important;
    color: white !important;
    border: 0 !important;
  }

  .selected {
    width: 260px;
    height: 55px;
    background-color: white;
    font-size: 18px;
    border-radius: 8px;
    border: 2px solid #FFB115;
    outline: none;
    font-family: 'Noto Sans', serif;
    color: #FFB115;
    font-weight: 400;
  }

  .custombutton:focus {
    outline: none;
  }
</style>
