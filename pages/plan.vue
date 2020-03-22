<template>
  <div class="container p-8 pb-0 background" style="background-image: url('/bg_plan.jpg')">
    <h1 class="title my-8">Dein Plan für heute</h1>
    <h2 class="mb-6">Was hast du heute vor?</h2>
    <CategoryTimeSlot
      v-for="item in timeSlots"
      v-bind:item="item"
      v-bind:key="item.id"
      v-on:click="onClick">
    </CategoryTimeSlot>
  </div>
</template>
<script>
import CategoryTimeSlot from '~/components/CategoryTimeSlot.vue';
import { categories } from '~/data/categories';

export default {
  components: {CategoryTimeSlot},
  methods: {
    onClick(category) {
      this.$router.push({
        name: 'category_details',
        query: { categoryId: category.id }
      });
    }
  },
  data() {
    return {
      timeSlots: []
    }
  },
  created() {
    const categoryIds = this.$route.query?.categoryIds || [];
    const selectedCategories = categoryIds.map(id => categories[id]);
    const defaultTimeSlots = [
      {id: 0, name: 'Morgens', category: selectedCategories[0]},
      {id: 1, name: 'Mittags', category: selectedCategories[1]},
      {id: 2, name: 'Abends', category: selectedCategories[2]}
    ];
    this.timeSlots = defaultTimeSlots;
  }
}
</script>
<style>
.header {
  display: flex;
}
</style>
