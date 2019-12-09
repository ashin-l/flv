<template>
  <div>
    <video ref="player" width="480" muted autoplay controls></video>
  </div>
</template>

<script>
import flvjs from "flv.js";
export default {
  props: {
    videoID: Number
  },
  data () {
    return {
      player: null
    }
  },
  mounted () {
    if (flvjs.isSupported()) {
      let video = this.$refs.player;
      if (video) {
        this.player = flvjs.createPlayer({
          type: "flv",
          isLive: true,
          //url: "ws://" + window.location.host + "/rtsp/${this.videoID}/"
          //url: `ws://sp.thfw.top/rtsp/${this.videoID}/`
          url: `ws://sp.thfw.top/rtsp/${this.videoID}?url=rtsp://admin:ai123456@192.168.160.101:554/cam/realmonitor?channel=1&subtype=0`
          //url: `ws://127.0.0.1:8888/rtsp/${this.videoID}/?url=rtsp://127.0.0.1:8554/changan.E01.sdp`
          //url: `ws://192.168.160.101:7681`
        });
        this.player.attachMediaElement(video);
        this.player.load();
        this.player.play();
      }
    }
  },
  beforeDestroy () {
    this.player.destory();
  }
}
</script>
