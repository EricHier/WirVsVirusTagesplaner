<template>
  <div>
    <h1>Plan Details</h1>
    <p>{{categoryDetails}}</p>
  </div>
</template>
<script>
import { category_details } from '~/data/category_details';

export default {
  components: {},
  methods: {
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
