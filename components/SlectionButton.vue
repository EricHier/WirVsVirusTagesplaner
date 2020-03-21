<template>
  <button v-on:click="sendclick" class="">
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
