<template>
  <ButtonDesign class="my-1" v-on:click="onClick">{{item.name}}</ButtonDesign>
</template>
<script>
import ButtonDesign from "./ButtonDesign";

export default {
  components: {ButtonDesign},
  props: ['item'],
  methods: {
    onClick() {
      this.$emit("click");
    }
  }
}
</script>
