<template>
  <div class="appbar-container text-center flex mb-4">
    <h3 class="title font-bold">{{appBarText}}</h3>
  </div>
</template>

<script>
export default {
  props: ['appBarText'],
}
</script>


<style>
  .appbar-container {
      background-color:blue;
      height: 60px;
  }

  h3 {
      width: 100%;
  }
</style>