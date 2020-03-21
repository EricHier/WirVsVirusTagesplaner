<template>
  <div>
    <ul>
      <CategoryItem
        v-for="item in list"
        v-bind:item="item"
        v-bind:key="item.id"
      >
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
          {"id": 1, name: 'Soziale Kontakte', checked: false},
          {"id": 2, name: 'Bewegung', checked: false},
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
