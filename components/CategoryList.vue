<template>
  <div>
    <ul>
      <CategoryItem
        v-for="item in list"
        v-bind:item="item"
        v-bind:key="item.name"
        v-on:click="onClick">
      </CategoryItem>
    </ul>
  </div>
</template>
<script>
import CategoryItem from '~/components/CategoryItem.vue';

export default {
  components: {
    CategoryItem
  },
  data() {
    return {
      list: [
        { name: 'Soziale Kontakte', checked: false },
        { name: 'Bewegung', checked: false },
        { name: 'Ernährung', checked: false },
        { name: 'Schlaf', checked: false },
        { name: 'Positiver Fokus', checked: false },
        { name: 'Kreatives', checked: false },
        { name: 'Entspannung', checked: false },
        { name: 'Produktiv sein', checked: false },
      ],
    }
  },
  methods: {
    onClick(e) {
      this.$emit("click", e);
    }
  }
}
</script>
