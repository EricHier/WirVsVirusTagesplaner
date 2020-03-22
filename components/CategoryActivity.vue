<template>
  <a v-bind:href="item.link" target="_blank" class="block border-2 border-orange text-center mx-12 my-2 p-4 nunito font-bold rounded-sm box">
    <img src="/link-24px.svg"  v-if="typeof item.link !== 'undefined'" width="24px" height="24px" class="mr-4  inline-block img">
    <h3 class="url-icon inline-block">{{item.name}}</h3>
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

  .img {
    display: inline-block;
    position: absolute;
    left: 0;
    margin-left: 4rem;
  }

</style>
