<template>
  <div v-on:click="onClick" class="w-full text-right">
    <button class="px-4 py-2 border larger border-black rounded-md outline-none">
      weiter
    </button>
  </div>
</template>
<script>
  export default {
    methods: {
      onClick() {
        this.$emit("click");
      }
    }
  }
</script>
<style>
  .larger {
    font-size: 20px;
  }
</style>
