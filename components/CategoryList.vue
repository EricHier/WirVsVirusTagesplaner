<template>
  <div>
    <ul>
      <ListItem v-for="item in list" v-bind:data="item"></ListItem>
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
  }
}
</script>
