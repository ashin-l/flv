<template>
  <div>
    <video ref="player" width="480" muted autoplay controls></video>
  </div>
</template>

<script>
import flvjs from "flv.js";
export default {
  props: {
    videoID: Number,
    vurl: String
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
          //url: `ws://127.0.0.1:50000/rtsp/${this.videoID}?url=rtsp://admin:admin123@192.168.160.109:554/h264/ch1/main/av_stream`
          //url: `ws://127.0.0.1:50000/rtsp/${this.videoID}?url=rtsp://admin:admin123@192.168.160.109:554/cam/realmonitor?channel=1&subtype=2`
          //url: `ws://127.0.0.1:50000/rtsp/${this.videoID}?url=rtsp://admin:ai123456@192.168.160.101:554/cam/realmonitor?channel=1&subtype=0`
          url: `ws://192.168.152.183:50000/rtsp/${this.videoID}?url=${this.vurl}`
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
