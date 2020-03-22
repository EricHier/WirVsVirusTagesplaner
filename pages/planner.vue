<template>
  <div class="container h-screen p-8 background">
    <h1 class="title my-8">Was hast du morgen vor?</h1>
    <div>
      <CategoryList ref="list"></CategoryList>
    </div>

    <WeiterButton v-on:click="onClick" class="absolute bottom-0 right-0 m-8" ></WeiterButton>
  </div>
</template>
<script>
import CategoryList from '~/components/CategoryList.vue';
import WeiterButton from "../components/WeiterButton";

export default {
  components: {
    WeiterButton,
    CategoryList
  },
  methods: {
    onClick() {
      this.$refs.list.submitCategoryList();
    }
  }
}
</script>

<!--TODO Nicht mehr als vier Sachen auswählen-->
