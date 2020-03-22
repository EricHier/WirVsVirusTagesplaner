<template>
  <div>
    <h1 class="title my-8">Was lief nicht gut?  </h1>
    <CategoryList
      v-bind:is-emit-click=true
      v-on:click="onClick"
    >
    </CategoryList>
  </div>
</template>
<script>
  import CategoryList from "../CategoryList";

  export default {
    components: {CategoryList},
    methods: {
      onClick(e) {
        this.$emit("submit", e.id);
      }
    }
  }
</script>
