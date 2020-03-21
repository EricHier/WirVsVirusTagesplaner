<template>
  <button v-on:click="sendclick" class="bg-transparent w-full hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded">
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
