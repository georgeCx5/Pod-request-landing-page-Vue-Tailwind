<script>
import logo from '@/assets/images/logo.svg?component'
import logoSpotify from '@/assets/images/spotify.svg?url'
import logoApple from '@/assets/images/apple-podcast.svg?url'
import logoGoogle from '@/assets/images/google-podcasts.svg?url'
import logoPocketCasts from '@/assets/images/pocket-casts.svg?url'
import imageMobile from '@/assets/images/image-host-mobile.jpg'

export default {
  data() {
    return {
      logoSpotify,
      logoApple,
      logoGoogle,
      logoPocketCasts,
      imgMobile: 'bg-[url("@/assets/images/image-host-mobile.jpg")]',
      imageMobile,
    }
  },
  components: {
    logo,
  }
}
</script>
<template>
  <main class=" relative h-[667px] bg-neo-darkest-blue font-chivo">
    <img class=" absolute opacity-[0.1]" :src="imageMobile" alt="imageMobile">
    <div class=" px-6 bg-neo-darkest-blue z-50">
      <logo />
      <h1 class=" text-white uppercase"><span class=" text-neo-green">Publish your podcasts</span> everywhere.</h1>
      <p class="  text-neo-very-pale-blue">
        Upload your audio to Pod with a single click. We’ll then distribute your podcast to Spotify,
        Apple Podcasts, Google Podcasts, Pocket Casts and more!
      </p>
      <div class=" flex justify-between items-center">
        <img class=" w-[56px]" :src="logoSpotify" alt="logoSpotify">
        <img class=" w-[45px]" :src="logoApple" alt="logoApple">
        <img class=" w-[73px]" :src="logoGoogle" alt="logoGoogle">
        <img class=" w-[77px]" :src="logoPocketCasts" alt="logoPocketCasts">
      </div>
      <div class=" flex flex-col gap-4">
        <input class=" h-[46px] px-6 bg-neo-dark-blue rounded-[28px]" type="email" placeholder="Email address">
        <button class=" h-[46px] bg-neo-green text-neo-darkest-blue rounded-[28px]" type="submit">Request access</button>
      </div>
    </div>
  </main>
</template>