<template>
  <div>
    <p class="w-screen mt-4 border-b-2 pl-8 mb-4 -ml-8 time-slot-text nunito border-orange">{{item.genitiv}}:</p>

    <div v-if="item.category" class="text-center">
      <SelectionButton
        class="my-1"
        v-on:click="onClick"
        >
        {{item.category.name}}
      </SelectionButton>
    </div>
    <div v-else class="text-center">
      <p>Nicht ausgewählt.</p>
    </div>
  </div>
</template>
<script>
import SelectionButton from '~/components/SelectionButton.vue';

export default {
  components: {SelectionButton},
  props: ['item'],
  methods: {
    onClick() {
      this.$emit("click", this.item);
    }
  }
}
</script>
<style scoped>
.time-slot-text {
  width: 100vw;
  font-weight: bold;
  font-size: 18px;
  color: #FFB115;
}
</style>
