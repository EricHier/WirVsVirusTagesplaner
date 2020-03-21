<template>
  <div>
    <h1>Plan your day</h1>
    <ListItem v-for="item in list" v-bind:data="item"></ListItem>
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
        {name: 'Arbeiten', check: false},
        {name: 'Sport', check: true}
      ],
    }
  }
}
</script>
