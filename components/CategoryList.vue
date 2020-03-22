<template>
  <div>
    <ul>
      <CategoryItem
        v-for="item in list"
        v-bind:item="item"
        v-bind:key="item.id"
        v-on:click="onClick">
      </CategoryItem>
    </ul>
    <WeiterButton v-if="!isEmitClick" v-on:click="submitCategoryList">Los</WeiterButton>

  </div>
</template>
<script>
import CategoryItem from '~/components/CategoryItem.vue';
import WeiterButton from "~/components/WeiterButton.vue";
import { categories } from '~/data/categories';

export default {
  props: {
    isEmitClick: Boolean
  },
  components: {
    CategoryItem, WeiterButton
  },
  methods: {
    submitCategoryList(clickEvent) {
      const filtered = this.list.filter(function(x) { return x.checked; });

      this.$router.push({
        name: 'plan',
        query: { categoryIds: filtered.map(x => x.id) }
      });
    },
    onClick(e) {
      this.$emit("click", e);
    }
  },
  data() {
    return {
      list: categories
    }
  }
}
</script>
