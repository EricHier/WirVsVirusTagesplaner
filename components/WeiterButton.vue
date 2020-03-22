<template>
  <div class="w-full flex justify-end px-8 fixed bottom-0 right-0 py-8" v-bind:class="{'justify-between' : back, 'background-seethrough' : seethrough}" >
    <button v-on:click="onClickBack" v-if="back" class="px-4 py-2 larger background-ouryellow text-white outline-none">
      zurück
    </button>
    <button v-on:click="onClick" v-if="weiter" class="px-4 py-2 larger background-ouryellow text-white outline-none">
      weiter
    </button>
  </div>
</template>
<script>
  export default {
    props: {
      back: Boolean,
      weiter: {
        type: Boolean,
        default: true
      },
      seethrough: Boolean
    },
    methods: {
      onClickBack() {
        this.$emit("back");
      },
      onClick() {
        this.$emit("click");
      }
    }
  }
</script>
<style>
  .larger {
    font-size: 20px;
  }

  .background-ouryellow {
    background-color: #F57840;
    height: 55px;
    width: 105px;
    border-radius: 8px;
  }

  .background-seethrough {
    background-color: #ffffffbf;
  }
</style>
