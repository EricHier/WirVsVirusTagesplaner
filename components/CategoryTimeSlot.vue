<template>
  <div>
    <h2>{{item.genitiv}}</h2>
    <div v-if="item.category">
      <SelectionButton
        class="my-1"
        v-on:click="onClick"
        >
        {{item.category.name}}
      </SelectionButton>
    </div>
    <div v-else>
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
