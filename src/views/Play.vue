<template>
  <div class="player">
    <TopBar :relatedVideos="relatedVideos" />
    <MainPlayer :currentVideo="currentVideo" />
  </div>
</template>

<script>
// import ytdl from 'ytdl-core';
import axios from 'axios';
import TopBar from '../components/media player/TopBar';
import MainPlayer from '../components/media player/MainPlayer';

export default {
  components: {
    TopBar,
    MainPlayer,
  },
  data() {
    return {
      relatedVideos: [],
      currentVideo: {},
      // audioSource: '',
    };
  },
  methods: {
    getRelatedVideos() {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            part: 'snippet',
            type: 'video',
            maxResults: '25',
            videoCategoryId: '10',
            relatedToVideoId: this.$route.params.id,
            key: process.env.VUE_APP_API_KEY,
          },
        })
        .then((result) => (this.relatedVideos = result.data.items));
    },
    getCurrentlyPlayingVideo() {
      axios
        .get('https://www.googleapis.com/youtube/v3/videos', {
          params: {
            part: 'snippet',
            videoCategoryId: '10',
            id: this.$route.params.id,
            key: process.env.VUE_APP_API_KEY,
          },
        })
        .then((result) => (this.currentVideo = result.data.items[0]));
    },
    // getAudioSource(id) {
    //   ytdl.getInfo(id).then((info) => console.log(info));
    // },
  },
  watch: {
    $route(to) {
      if (to.name === 'Play') {
        this.getCurrentlyPlayingVideo();
      }
    },
  },
  mounted() {
    // this.getAudioSource(this.$route.params.id);
    this.getRelatedVideos();
    this.getCurrentlyPlayingVideo();
  },
};
</script>

<style scoped>
.player {
  width: 100%;
  max-height: 100%;
  overflow: hidden !important;
}
</style>
