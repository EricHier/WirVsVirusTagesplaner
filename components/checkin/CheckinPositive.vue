<template>
  <div>
    <h1 class="title my-8">Was lief gut?  </h1>
    <CategoryList v-on:click="test"></CategoryList>
  </div>
</template>
<script>
  import CategoryList from "../CategoryList";

  export default {
    components: {CategoryList},
    methods: {
      test(e) {
        console.log(e);
      }
    }
  }
</script>
