<template>
  <div class="container p-8 pb-0 background" v-bind:style="{'background-image' : 'url(' + background + ')'}">
    <Splashscreen v-if="screenIndex === 0"></Splashscreen>

    <CheckinMood v-if="screenIndex === 1" v-on:data="newMoodData" v-bind:inputValue="checkinMood"> </CheckinMood>
    <CheckinPositive v-if="screenIndex === 2" v-on:data="newPositiveData" v-bind:data="checkinPositive" v-on:show="weiterButton = true"></CheckinPositive>
    <CheckinNegative v-if="screenIndex === 3" v-on:data="newNegativeData" v-bind:data="checkinNegative" v-on:show="weiterButton = true"></CheckinNegative>

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
      this.screenIndex++;
    },
    newMoodData(data) {
      this.checkinMood = data;
    },
    newPositiveData (data) {
      this.checkinPositive = data;

      if (data.length >= 1)
        this.weiterButton = true;
    },
    newNegativeData (data) {
      this.checkinNegative = data;

      if (data.length >= 1)
        this.weiterButton = true;
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
