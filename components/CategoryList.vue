<template>
  <div>
    <CategoryItem
      v-for="item in listItems"
      v-bind:item="item"
      v-bind:key="item.id"
      v-on:click="onClick">
    </CategoryItem>
  </div>
</template>
<script>
import CategoryItem from '~/components/CategoryItem.vue';
import WeiterButton from "~/components/WeiterButton.vue";
import { categories } from '~/data/categories';

export default {
  components: {
    CategoryItem
  },
  methods: {
    submitCategoryList(clickEvent) {
      const filtered = this.listItems.filter(function(x) { return x.checked; });

      this.$router.push({
        name: 'plan',
        query: { categoryIds: filtered.map(x => x.id) }
      });
    },
    getData() {
      return this.listItems;
    },
    onClick(e) {
      let selectedItems =  this.listItems.filter((value) => value.checked);
      let selected = selectedItems.length;
      if (selected > 3)
        e.checked = false;

      e.selectedItems = selectedItems;

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
