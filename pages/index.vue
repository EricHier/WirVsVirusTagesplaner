<template>
  <div>
    <Splashscreen v-if="screenIndex === 0"></Splashscreen>

    <CheckinMood v-if="screenIndex === 1" v-on:submit="submitCheckinMood"></CheckinMood>
    <CheckinPositive v-if="screenIndex === 2" v-on:submit="submitCheckinPositive"></CheckinPositive>
    <CheckinNegative v-if="screenIndex === 3" v-on:submit="submitCheckinNegative"></CheckinNegative>

  </div>
</template>

<script>
import Splashscreen from '~/components/Splashscreen.vue'
import CheckinMood from '~/components/checkin/CheckinMood.vue'
import CheckinPositive from '~/components/checkin/CheckinPositive.vue'
import CheckinNegative from '~/components/checkin/CheckinNegative.vue'

export default {
  components: {
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
    }
  },
  watch: {
    screenIndex (newVal) {
      if (newVal >= 4) {
        this.$route.push("/planner");
      }
    }
  },
  created() {
    let self = this;

    setTimeout(() => {
      self.screenIndex = 1
    }, 1000);
  }
}
</script>
