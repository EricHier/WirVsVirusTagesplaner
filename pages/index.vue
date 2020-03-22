<template>
  <div class="container p-8 background">
    <Splashscreen v-if="screenIndex === 0"></Splashscreen>

    <CheckinMood ref="checkinmood" v-if="screenIndex === 1" v-on:submit="submitCheckinMood"></CheckinMood>
    <CheckinPositive v-if="screenIndex === 2" v-on:submit="submitCheckinPositive"></CheckinPositive>
    <CheckinNegative v-if="screenIndex === 3" v-on:submit="submitCheckinNegative"></CheckinNegative>

    <WeiterButton v-if="screenIndex === 1" class="absolute bottom-0 right-0 m-8" v-on:click="onClick"></WeiterButton>
  </div>
</template>

<script>
import Splashscreen from '~/components/Splashscreen.vue'
import CheckinMood from '~/components/checkin/CheckinMood.vue'
import CheckinPositive from '~/components/checkin/CheckinPositive.vue'
import CheckinNegative from '~/components/checkin/CheckinNegative.vue'
import WeiterButton from "../components/WeiterButton";

export default {
  components: {
    WeiterButton,
    Splashscreen, CheckinMood, CheckinPositive, CheckinNegative
  },
  data() {
    return {
      screenIndex: 0,
      checkinMood: {},
      checkinPositive: {},
      checkinNegative: {}
    }
  },
  methods: {
    submitCheckinMood(props) {
      this.checkinMood = props;
      this.screenIndex++;
    },
    submitCheckinPositive(props) {
      this.checkinPositive = props;
      this.screenIndex++;
    },
    submitCheckinNegative(props) {
      this.checkinNegative = props;
      this.screenIndex++;
    },
    onClick() {
      this.$refs.checkinmood.click();
    }
  },
  watch: {
    screenIndex (newVal) {
      if (newVal >= 4) {
        this.$router.push({
          name: 'planner',
          query: { categoryIds: [this.checkinPositive, this.checkinNegative] }
        });
      }
    }
    // 375 - 812
  },
  created() {
    let self = this;

    setTimeout(() => {
      self.screenIndex = 1
    }, 1000);
  }
}
</script>
