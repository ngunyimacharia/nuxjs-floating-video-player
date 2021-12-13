<template>
  <div>
      <video
        id="floating-player"
        autoplay
        class="cld-video-player cld-video-player-skin-dark w-1/2 mx-auto h-96"
      >
      </video>
      <div class="w-4/5 mx-auto relative py-16 bg-white overflow-hidden">
        <dummy-content />
      </div>
  </div>
</template>

<script>

import DummyContent from "../components/DummyContent.vue"

export default {
  components:{
    DummyContent
  },
  mounted(){
    const cld = cloudinary.Cloudinary.new({ cloud_name: process.env.NUXT_ENV_CLOUDINARY_CLOUD_NAME, secure:true });
    var player = cld.videoPlayer(
      'floating-player',
      {
        controls:true,
        floatingWhenNotVisible: 'left',
      }
      );
    player.source('nuxtjs-floating-video-player/pexels-lisa-9963201.mp4');
  }
}
</script>
