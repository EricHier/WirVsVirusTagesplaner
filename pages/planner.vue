<template>
  <div>
    <h1>Was hast du morgen vor?</h1>
    <CategoryList></CategoryList>
  </div>
</template>
<script>
import CategoryList from '~/components/CategoryList.vue';

export default {
  components: {
    CategoryList
  }
}
</script>

<!--TODO Nicht mehr als vier Sachen auswählen-->
