<template>
  <div class="container p-8 background">
    <h1 class="title my-8">Dein Plan für heute</h1>
    <div>
      <h2>Morgens</h2>
      <p v-if="selectedCategories[0]">{{selectedCategories[0].name}}</p>
      <p v-else>Nicht ausgewählt.</p>
    </div>
    <div>
      <h2>Mittags</h2>
      <p v-if="selectedCategories[1]">{{selectedCategories[1].name}}</p>
      <p v-else>Nicht ausgewählt.</p>
    </div>
    <div>
      <h2>Abends</h2>
      <p v-if="selectedCategories[2]">{{selectedCategories[2].name}}</p>
      <p v-else>Nicht ausgewählt.</p>
    </div>
  </div>
</template>
<script>
import { categories } from '~/data/categories';

export default {
  data() {
    return {
      selectedCategories: []
    }
  },
  created() {
    const categoryIds = this.$route.query?.categoryIds || [];
    this.selectedCategories = categoryIds.map(id => categories[id]);
  }
}
</script>
<style>
  .header {
    display: flex;
  }
</style>
