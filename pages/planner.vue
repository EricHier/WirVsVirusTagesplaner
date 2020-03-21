<template>
  <div>
    <h1>Was hast du morgen vor?</h1>
    <ul>
      <ListItem v-for="item in list" v-bind:data="item"></ListItem>
    </ul>
  </div>
</template>
<script>
import ListItem from '~/components/plan/ListItem.vue'

export default {
  components: {
    ListItem
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
