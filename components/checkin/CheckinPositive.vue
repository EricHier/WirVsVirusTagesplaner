<template>
  <div>
    <h1 class="title my-8">Was lief gut?  </h1>
    <CategoryList
    v-on:click="onClick"
    ref="categorylist">
    </CategoryList>
  </div>
</template>
<script>
  import CategoryList from "../CategoryList";

  export default {
    components: {CategoryList},
    methods: {
      onClick(e) {
        this.$emit("show");
      },
      sendResult() {
        this.$emit("submit", this.$refs.categorylist.getData());
      }
    }
  }
</script>
