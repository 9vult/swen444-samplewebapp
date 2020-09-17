<template>
  <div class="home">
    <img alt="Kingston" src="@/assets/ktown.jpg">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <ConferenceInfo />
    <RegisterButton v-show="!regvis && regbtn" v-on:reg-show="regShow" />
    <RegisterFields v-show="regvis"            v-on:register-next="registerNext" />
    <Review         v-show="reviewvis"         v-on:go-back="goBack" v-bind:curRegistrant="curRegistrant"  />
  </div>
</template>

<script>
// @ is an alias to /src
import ConferenceInfo from '@/components/ConferenceInfo.vue'
import RegisterButton from '@/components/RegisterButton.vue'
import RegisterFields from '@/components/RegisterFields.vue'
import Review from '@/components/Review.vue'

export default {
  name: 'Home',
  components: {
    ConferenceInfo,
    RegisterButton,
    RegisterFields,
    Review
  },
  data() {
    return {
      curRegistrant: {},
      regvis: false,
      regbtn: true,
      reviewvis: false
    }
  },
  methods: {
    regShow() {
      this.regvis = !this.regvis;
      this.reviewvis = false;
      this.regbtn = false;
    },
    revShow() {
      this.reviewvis = !this.reviewvis;
    },
    registerNext(registrant) {
      this.curRegistrant = registrant;
      this.regShow()
      this.revShow()
    },
    goBack() {
      this.reviewvis = false;
      this.regvis = true;
    }
  }
}
</script>
