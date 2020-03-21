<template>
  <div class="container p-8 background">
    <h1 class="title my-8">Was hast du morgen vor?</h1>
    <CategoryList></CategoryList>
  </div>
</template>
<script>
import CategoryList from '~/components/CategoryList.vue';
import WeiterButton from "~/components/WeiterButton";

export default {
  components: {
    CategoryList
  }
}
</script>

<!--TODO Nicht mehr als vier Sachen auswählen-->
