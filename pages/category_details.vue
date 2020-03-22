<template>
  <div>
    <div class="fixed top-0 left-0 w-screen h-screen" style="background-image: url('/bg_plan.jpg'); z-index: -2"></div>

    <div style="background-image: url('/Weisse_Flaeche.svg'); padding-bottom: 7rem;" class="p-8 mt-56">
      <h1 class="title mt-12 mb-2 text-center">{{title}}</h1>
      <h2 class="text-center">{{question}}</h2>

      <p class="mt-4 border-b-2 pl-8 mb-4 -ml-8 category-name nunito border-orange"> {{categoryDetails.name}}</p>

      <div class="bg-white w-screen -ml-8">
        <CategoryActivity
          v-for="item in categoryDetails.activities"
          v-bind:item="item"
          v-bind:key="item.category_id"
          v-on:click="onClick">
        </CategoryActivity>
      </div>
    </div>
  </div>
</template>
<script>
import CategoryActivity from '~/components/CategoryActivity.vue';
import { category_details } from '~/data/category_details';

export default {
  components: {CategoryActivity},
  methods: {
    onClick(activity) {
      console.log('activity', activity);
    }
  },
  data() {
    return {
      categoryDetails: {},
      title: "",
      question: ""
    }
  },
  created() {
    const categoryId = this.$route.query.categoryId;
    this.title = this.$route.query.title;
    this.question = this.$route.query.question;

    for(const details of category_details) {
      if(details.category_id == categoryId) {
        this.categoryDetails = details;
      }
    }
  }
}
</script>
<style>
  .category-name {
    width: 100vw;
    font-weight: bold;
    font-size: 18px;
    color: #FFB115;
  }
</style>
