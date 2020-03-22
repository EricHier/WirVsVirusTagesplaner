<template>
  <a v-bind:href="item.link" class="block border-2 border-orange mx-6 my-2 p-4 nunito font-bold rounded-sm box">
    <h3>{{item.name}}</h3>
  </a>
</template>
<script>
export default {
  props: ['item']
}
</script>
<style>
  .box {
    border-radius: 8px;
    color: #FFB115;
  }
</style>
