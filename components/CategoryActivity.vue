<template>
  <a v-bind:href="item.link" class="flex justify-between block border-2 border-orange mx-12 my-2 p-4 nunito font-bold rounded-sm box">
    <img src="/link-24px.svg" v-if="typeof item.link !== 'undefined'" width="24px" height="24px" class="mr-4">
    <h3 class="text-center url-icon">{{item.name}}</h3>
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
