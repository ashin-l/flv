<template>
  <div>
    <h1>RTMP Video</h1>
    <!-- <video id="my-video" class="video-js" controls autoplay preload="auto" width="640" height="320" tech="flash">
            <source src="rtmp://127.0.0.1/live/" type="rtmp/flv">
        </video> -->
    <!-- <embed src="/static/video-js.swf"> -->
    <!--
    <div v-for="i in 3" :key="`video-${i}`" class="flex-row">
      <video-player :videoID="(i - 1) * 3 + 1"></video-player>
      <video-player :videoID="(i - 1) * 3 + 2"></video-player>
      <video-player :videoID="(i - 1) * 3 + 3"></video-player>
    </div>
    -->
    <div class="flex-row">
      <video-player :videoID="101" :vurl="vurl1"></video-player>
    </div>
    <div class="flex-row">
      <video-player :videoID="401" :vurl="vurl2"></video-player>
    </div>
  </div>
</template>

<script>
import FlvPlayerVue from './FlvPlayer.vue';
export default {
  components: {
    "video-player": FlvPlayerVue
  },
  data () {
    return {
      vurl1: encodeURIComponent("rtsp://admin:ai123456@192.168.160.101:554/h264/ch1/main/av_stream"),
      vurl2: encodeURIComponent("rtsp://admin:admin123@192.168.160.109:554/cam/realmonitor?channel=1&subtype=0")
    }
  },
  mounted () {

  }
}
</script>

<style>
.flex-row {
  display: flex;
  flex-direction: row;
}

.flex-row > div {
  margin-right: 5px;
}
</style>
