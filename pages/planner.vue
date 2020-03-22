<template>
  <div class="container p-8 pb-0 background" style="background-image: url('/bg_list.jpg')">
    <div style="background-image: url('/Weisse_Flaeche.svg'); padding-bottom: 7rem; " class="-mx-8 mt-20">

      <h1 class="title mt-12">Was hast du morgen vor?</h1>
      <p class="my-4 text-center nunito">Bitte drei auswählen:</p>
      <CategoryList
        ref="categorylist"
        v-on:notthree="notThree">
      </CategoryList>
    </div>

    <WeiterButton v-bind:back="false" v-bind:seethrough="true" v-bind:weiter="weiterButton" v-on:click="onClick">
    </WeiterButton>
  </div>
</template>
<script>
  import CategoryList from '~/components/CategoryList.vue';
  import WeiterButton from "../components/WeiterButton";

  export default {
    components: {
      WeiterButton,
      CategoryList
    },
    data() {
      return {
        weiterButton: false
      }
    },
    methods: {
      onClick() {
        this.$refs.categorylist.submitCategoryList();
      },
      notThree(e) {
        this.weiterButton = e;
      }
    },
    mounted() {
      let categoryIds = this.$route.query?.categoryIds || [];
      categoryIds = categoryIds.filter((item) => categoryIds.indexOf(item) < 2);
      this.$refs.categorylist.setSelected(categoryIds);
    }
  }
</script>

<!--TODO Nicht mehr als vier Sachen auswählen-->
