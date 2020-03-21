<template>
  <div>
    <ul>
      <CategoryItem
        v-for="item in list"
        v-bind:item="item"
        v-bind:key="item.id">
      </CategoryItem>
    </ul>
    <button v-on:click="submitCategoryList">Los</button>
  </div>
</template>
<script>
import CategoryItem from '~/components/CategoryItem.vue';

export default {
  components: {
    CategoryItem
  },
  methods: {
    submitCategoryList(clickEvent) {
      const filtered = this.list.filter(function(x) { return x.checked; });

      this.$router.push({
        name: 'plan',
        query: { categoryIds: filtered.map(x => x.id) }
      });
    }
  },
  data() {
    return {
      list: [
        {"id": 1, name: 'Soziale Kontakte', checked: true},
        {"id": 2, name: 'Bewegung', checked: true},
        {"id": 3, name: 'Ernährung', checked: false},
        {"id": 4, name: 'Schlaf', checked: false},
        {"id": 5, name: 'Positiver Fokus', checked: false},
        {"id": 6, name: 'Kreatives', checked: false},
        {"id": 7, name: 'Entspannung', checked: false},
        {"id": 8, name: 'Produktiv sein', checked: false},
      ],
    }
  }
}
</script>
