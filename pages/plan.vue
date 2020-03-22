<template>
  <div>
    <div class="fixed top-0 left-0 w-screen h-screen" style="background-image: url('/bg_plan.jpg'); z-index: -2"></div>

    <div style="background-image: url('/Weisse_Flaeche.svg'); padding-bottom: 7rem;" class="p-8 mt-56">
      <h1 class="title mb-2 text-center" style="margin-top: 4rem">Dein Plan für heute</h1>
      <h2 class="text-center">Was hast du heute vor?</h2>

      <CategoryTimeSlot
        v-for="item in timeSlots"
        v-bind:item="item"
        v-bind:key="item.id"
        v-on:click="onClick">
      </CategoryTimeSlot>
    </div>
  </div>
</template>
<script>
import CategoryTimeSlot from '~/components/CategoryTimeSlot.vue';
import { categories } from '~/data/categories';

export default {
  components: {CategoryTimeSlot},
  methods: {
    onClick(event) {
      this.$router.push({
        name: 'category_details',
        query: {
          categoryId: event?.category?.id,
          title: event.genitiv,
          question: `Was hast du am ${event.name} vor?`
        }
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
      {id: 0, name: 'Morgen', genitiv: 'Morgens', category: selectedCategories[0]},
      {id: 1, name: 'Mittag', genitiv: 'Mittags', category: selectedCategories[1]},
      {id: 2, name: 'Abend', genitiv: 'Abends', category: selectedCategories[2]}
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
