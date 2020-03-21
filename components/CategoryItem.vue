<template>
  <SelectionButton class="my-1" v-on:click="onClick">{{item.name}}</SelectionButton>
</template>
<script>
import SelectionButton from "./SelectionButton";

export default {
  components: {SelectionButton},
  props: ['item'],
  methods: {
    onClick() {
      this.item.checked = !this.item.checked;
      this.$emit("click", this.item);
    }
  }
}
</script>
