<template>
  <div class="container p-8 background">
    <h1 class="title my-8">Dein Plan für heute</h1>
    <div>
      <h2>Morgens</h2>
      <p v-if="categoryIds[0]">{{categoryIds[0]}}</p>
      <p v-else>Nichts</p>
    </div>
    <div>
      <h2>Mittags</h2>
      <p v-if="categoryIds[1]">{{categoryIds[1]}}</p>
      <p v-else>Nichts</p>
    </div>
    <div>
      <h2>Abends</h2>
      <p v-if="categoryIds[2]">{{categoryIds[2]}}</p>
      <p v-else>Nichts</p>
    </div>
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
    this.categoryIds = this.$route.query?.categoryIds || [];
  }
}
</script>
<style>
  .header {
    display: flex;
  }
</style>
