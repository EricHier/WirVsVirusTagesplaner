<template>
  <div style="background-image: url('/Weisse_Flaeche.svg'); padding-bottom: 7rem; " class="-mx-8 mt-20">

    <h1 class="title my-8 mt-12">Womit bist du heute<br> zufrieden? </h1>
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
