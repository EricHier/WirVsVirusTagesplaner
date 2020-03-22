<template>
  <div class="container p-8 pb-0 background" v-bind:style="{'background-image' : 'url(' + background + ')'}">
    <Splashscreen v-if="screenIndex === 0"></Splashscreen>

    <CheckinMood ref="checkinmood" v-if="screenIndex === 1" v-on:submit="submitCheckinMood" v-bind:inputValue="checkinMood"> </CheckinMood>
    <CheckinPositive ref="checkinpositive" v-if="screenIndex === 2" v-on:submit="submitCheckinPositive" v-on:show="weiterButton = true" v-bind:data="checkinPositive"></CheckinPositive>
    <CheckinNegative v-if="screenIndex === 3" v-on:submit="submitCheckinNegative"  v-on:show="weiterButton = true"></CheckinNegative>

    <WeiterButton v-if="screenIndex >= 1" v-bind:back="screenIndex >=2" v-on:back="screenIndex--" v-bind:seethrough="screenIndex >= 2" v-bind:weiter="weiterButton || screenIndex == 1" v-on:click="onClick"></WeiterButton>
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
    WeiterButton, Splashscreen, CheckinMood, CheckinPositive, CheckinNegative
  },
  data() {
    return {
      screenIndex: 0,
      weiterButton: false,
      checkinMood: 2,
      checkinPositive: [],
      checkinNegative: [],
      background: "/bg_slider.jpg"
    }
  },
  methods: {
    onClick()  {
      if (this.screenIndex === 1)
        this.$refs.checkinmood.sendResult();
      else if (this.screenIndex === 2)
        this.$refs.checkinpositive.sendResult();
    },
    submitCheckinMood(props) {
      this.checkinMood = props;
      this.screenIndex++;
    },
    submitCheckinPositive(props) {
      this.checkinPositive = props;
      this.screenIndex++;
      this.weiterButton = false;
    },
    submitCheckinNegative(props) {
      this.checkinNegative = props;
      this.screenIndex++;
    }
  },
  watch: {
    screenIndex (newVal) {
      if(newVal >= 2) {
        this.background = "/bg_list.jpg";
      } else {
        this.background = "/bg_slider.jpg";
      }

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
    }, 3000);
  }
}
</script>
