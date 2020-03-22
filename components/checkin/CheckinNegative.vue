<template>
  <div>
    <h1 class="title my-8">Was lief nicht gut?  </h1>
    <CategoryList
      v-on:click="onClick"
      ref="categorylistnegative">
    </CategoryList>
  </div>
</template>
<script>
  import CategoryList from "../CategoryList";

  export default {
    components: {CategoryList},
    methods: {
      onClick(e) {
        console.log(e);
        this.$emit("show");
      }
    }
  }
</script>
