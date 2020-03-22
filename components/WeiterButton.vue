<template>
  <div class="w-full flex justify-end px-8 fixed bottom-0 right-0 py-8" v-bind:class="{'justify-between' : back, 'background-seethrough' : seethrough}" >
    <button v-on:click="onClickBack" v-if="back" class="custombutton nunito px-4 py-2 larger background-ouryellow text-white outline-none">
      zurück
    </button>
    <button v-if="weiter && !disabled" v-on:click="onClick" class="nunito  px-4 py-2 larger background-ouryellow text-white outline-none">
      weiter
    </button>
    <button v-if="weiter && disabled" class="nunito px-4 py-2 larger background-ouryellow text-white outline-none opacity-50 cursor-not-allowed" disabled>
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
      disabled: Boolean,
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
<style scoped>
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

  .custombutton {
    background-color: white !important;
    font-weight: 400 !important;
    color: #F57840 !important;
    border: 2px solid #F57840 !important;
  }
</style>
