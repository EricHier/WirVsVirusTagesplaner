<template>
  <div>
    <Splashscreen v-if="screenIndex === 0"></Splashscreen>

    <CheckinMood v-if="screenIndex === 1"></CheckinMood>
    <CheckinPositive v-if="screenIndex === 2"></CheckinPositive>
    <CheckinNegative v-if="screenIndex === 3"></CheckinNegative>

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
      screenIndex: 0
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
