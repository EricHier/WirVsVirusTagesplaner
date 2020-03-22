<template>
  <div>
    <h1>Plan Details</h1>
    <h2>{{categoryDetails.name}}</h2>
    <CategoryActivity
      v-for="item in categoryDetails.activities"
      v-bind:item="item"
      v-bind:key="item.category_id"
      v-on:click="onClick">
    </CategoryActivity>
  </div>
</template>
<script>
import CategoryActivity from '~/components/CategoryActivity.vue';
import { category_details } from '~/data/category_details';

export default {
  components: {CategoryActivity},
  methods: {
    onClick(activity) {
      console.log('activity', activity);
    }
  },
  data() {
    return {
      categoryDetails: {}
    }
  },
  created() {
    const categoryId = this.$route.query.categoryId;

    for(const details of category_details) {
      if(details.category_id == categoryId) {
        this.categoryDetails = details;
      }
    }
  }
}
</script>
