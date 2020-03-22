<template>
  <div style="background-image: url('/Weisse_Flaeche.svg')" class="w-screen h-screen mt-20">

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
    props: ["data"],
    methods: {
      onClick(e) {
        this.$emit("data", this.$refs.categorylist.getData());
      }
    },
    mounted() {
      this.$refs.categorylist.setSelected(this.data);
    }
  }
</script>
