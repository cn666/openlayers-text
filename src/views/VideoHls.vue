
<!--<script lang="ts" setup>-->
<!--import {onMounted, ref} from 'vue'-->
<!--import videojs from 'video.js'-->
<!--let player = ref(null)-->
<!--let  getVideo = ()=> {-->

<!--}-->
<!--onMounted(() => {-->
<!--  getVideo()-->
<!--})-->
<!--</script>-->

<script>
import videojs from 'video.js'
export default  {
  data() {
    return {
      player: null
    }
  },
  methods: {
    loadPlayer() {
     this.player =  videojs('example_video_1', {
        autoplay: true,
        bigPlayButton: true,
        textTrackDisplay: false,
        posterImage: false,
        errorDisplay: false,
        controls: true,
        hls: {
          withCredentials: true
        }
      },  function onPlayerReady(){
       console.log('ready', this)
       console.log('ready --player',  this.player)
      })

    },
    handlePlay() {
      this.player.play()
    }

  },
  mounted() {
    this.loadPlayer()
  }
}
</script>


<template>
<div class="video" @click="handlePlay">点击播放</div>
  <video id="example_video_1" class="video-js" controls preload="none" width="640" height="360"  >
<!--    <source src="http://111.21.13.122:4000/hls/826de61ffa6947f293a89313760df374.m3u8" type="application/x-mpegURL">-->
<!--    <source src="http://amdlive.ctnd.com.edgesuite.net/arirang_1ch/smil:arirang_1ch.smil/playlist.m3u8" type="application/x-mpegURL">-->
    <source src="http://ebsonairios.ebs.co.kr/ebsutablet500k/_definst_/tablet500k/chunklist_w1965791004.m3u8" type="application/x-mpegURL">
<!--    <source src="http://192.168.4.45:8000/hls/test.m3u8" type="application/x-mpegURL">-->
  </video>
</template>

<style scoped>
.video {
  width: 500px;
  height: 500px;
  border: 1px solid red;
}
</style>
