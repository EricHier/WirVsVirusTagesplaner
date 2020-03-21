<template>
  <div>
    <h1>Plan</h1>
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
