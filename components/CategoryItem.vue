<template>
  <SelectionButton class="my-1" v-on:click="onClick">{{item.name}}</SelectionButton>
</template>
<script>
import SelectionButton from "./SlectionButton";

export default {
  components: {SelectionButton},
  props: ['item'],
  methods: {
    onClick() {
      this.$emit("click");
    }
  }
}
</script>
