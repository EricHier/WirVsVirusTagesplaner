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
      list: [
        {id: 0, name: 'Soziale Kontakte', checked: false},
        {id: 1, name: 'Bewegung', checked: false},
        {id: 2, name: 'Ernährung', checked: false},
        {id: 3, name: 'Schlaf', checked: false},
        {id: 4, name: 'Positiver Fokus', checked: false},
        {id: 5, name: 'Kreatives', checked: false},
        {id: 6, name: 'Entspannung', checked: false},
        {id: 7, name: 'Produktiv sein', checked: false},
      ],
    }
  }
}
</script>
