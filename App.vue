<script>
import logo from '@/assets/images/logo.svg?component'
import logoSpotify from '@/assets/images/spotify.svg?url'
import logoApple from '@/assets/images/apple-podcast.svg?url'
import logoGoogle from '@/assets/images/google-podcasts.svg?url'
import logoPocketCasts from '@/assets/images/pocket-casts.svg?url'
import BgDots from './components/BgDots.vue'

export default {
  data() {
    return {
      logoSpotify,
      logoApple,
      logoGoogle,
      logoPocketCasts,
      imgMobile: 'bg-[url("@/assets/images/image-host-mobile.jpg")]',
      imgTablet: 'tb:bg-[url("@/assets/images/image-host-tablet.jpg")]',
      imgDesktop: 'dsk:bg-[url("@/assets/images/image-host-desktop.jpg")]',
      rgxEmail: new RegExp(/^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/),
      emailValue: '',
      stateValue: 'default',
    }
  },
  components: {
    logo,
    BgDots,
  },
  methods: {
    checkEmail() {
      if (this.emailValue.length <= 0) {
        this.stateValue = 'empty';
        return;
      }
      if (this.rgxEmail.test(this.emailValue)) {
        this.stateValue = 'success';
        this.emailValue = '';
      } else {
        this.stateValue = 'error';
      }
    }
  },
  computed: {
    errorState() {
      if (this.stateValue == 'empty' || this.stateValue == 'error') {
        return true;
      } else {
        return false;
      }
    }
  }
}
</script>
<template>
  <body class=" h-screen bg-neo-darkest-blue">
    <main :class="` relative h-[667px] tb:h-[1024px] dsk:h-[900px] bg-neo-darkest-blue font-chivo`">
      <div
        class="absolute tb:right-0 dsk:top-[130px] w-full tb:w-[491px] dsk:w-[888px] h-full tb:h-[767px] dsk:h-[640px] bg-cover tb:bg-auto tb:bg-no-repeat opacity-[.15] tb:opacity-[1]"
        :class="`${imgMobile} ${imgTablet} ${imgDesktop}`">
      </div>
      <BgDots />
      <!-- Main Content -->
      <div
        class=" relative flex flex-col items-center tb:items-start gap-[57px] tb:gap-[152px] dsk:gap-[103px] pt-[62px] tb:pt-[50px] dsk:pt-[102px] px-6 tb:px-10">
        <logo />
        <div
          class=" flex flex-col gap-8 tb:gap-10 max-w-[425px] tb:max-w-none tb:w-[635px] dsk:w-[723px] tb:h-[509px] tb:pt-[93px] tb:bg-neo-darkest-blue z-50">
          <div class=" flex flex-col gap-4 tb:gap-8 dsk:gap-6 text-center tb:text-left">
            <h1 class=" text-white uppercase text-[26px] tb:text-[48px] dsk:text-[52px] leading-[38px] tb:leading-[56px] dsk:leading-[62px] font-thin">
              <span class=" text-neo-green">
                Publish your podcasts
              </span> everywhere.
            </h1>
            <p
              class=" tb:w-[445px] text-neo-very-pale-blue text-[15px] tb:text-[18px] leading-[25px] tb:leading-[28px] font-extralight">
              Upload your audio to Pod with a single click. We’ll then distribute your podcast to Spotify,
              Apple Podcasts, Google Podcasts, Pocket Casts and more!
            </p>
          </div>
          <div class=" flex flex-col tb:flex-col-reverse items-center tb:items-start gap-12 tb:gap-16">
            <div class=" flex justify-between tb:justify-start items-center tb:gap-10 w-full opacity-[.6]">
              <img class=" w-[56px] tb:w-[96px]" :src="logoSpotify" alt="logoSpotify">
              <img class=" w-[45px] tb:w-[78px]" :src="logoApple" alt="logoApple">
              <img class=" w-[73px] tb:w-[125px]" :src="logoGoogle" alt="logoGoogle">
              <img class=" w-[77px] tb:w-[129px]" :src="logoPocketCasts" alt="logoPocketCasts">
            </div>
            <div class=" tb:relative flex flex-col items-center gap-4 text-[14px] leading-7 font-bold">
              <div class=" flex flex-col gap-2 w-[327px] tb:w-[427px]">
                <input
                  class=" h-[46px] tb:h-[56px] px-6 bg-neo-dark-blue text-neo-white focus:outline-none rounded-[28px]"
                  type="email" placeholder="Email address" v-model="emailValue">
                <div v-show="errorState" class=" px-6 text-neo-red text-[12px] leading-[14px] font-bold">
                  <h5 v-show="stateValue == 'empty'">Oops! Please add your email</h5>
                  <h5 v-show="stateValue == 'error'">Oops! Please check your email</h5>
                </div>
              </div>
              <button @click="checkEmail()"
                class=" tb:absolute tb:right-[5px] tb:top-[5px] w-[327px] tb:w-[162px] h-[46px] bg-neo-green text-neo-darkest-blue rounded-[28px]"
                type="submit">
                Request access
              </button>
            </div>
          </div>
        </div>
      </div>
    </main>
</body></template>