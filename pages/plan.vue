<template>
  <div class="container p-8 background">
    <h1 class="title my-8">Dein Plan für heute</h1>
  </div>
</template>
<script>
export default {
  data() {
    return {
      categoryIds: []
    }
  },
  created() {
    console.log(this.$route.query.categoryIds);
  }
}
</script>
<style>
  .header {
    display: flex;
  }
</style>
