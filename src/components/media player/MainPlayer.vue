<template>
  <div class="main-player">
    <v-row class="mt-5" justify="center">
      <v-avatar class="avatar-container" size="200">
        <v-img :src="currentVideo.snippet.thumbnails.medium.url"></v-img>
      </v-avatar>
    </v-row>
    <v-row class="mt-8" justify="center">
      <div class="song-info">
        <h1>{{ currentVideo.snippet.title.substr(0, 35) + '...' }}</h1>
        <p>{{ currentVideo.snippet.channelTitle }}</p>
      </div>
    </v-row>
    <v-row class="mx-auto mt-4 direction" style="max-width:90%" align="center">
      <div class="timings">
        <span>01:53</span>
        <span class="color">03:24</span>
      </div>
      <v-progress-linear
        color="#ad1d45"
        class="mt-4"
        rounded
        value="55"
      ></v-progress-linear>
    </v-row>
    <v-row class="controls mt-5 mx-auto" style="max-width:80%">
      <v-col class="first" cols="9">
        <v-btn dark fab small>
          <v-icon>mdi-skip-previous</v-icon>
        </v-btn>
        <v-btn dark fab large>
          <v-icon>mdi-play</v-icon>
        </v-btn>
        <v-btn dark fab small>
          <v-icon>mdi-skip-next</v-icon>
        </v-btn>
      </v-col>
      <v-col class="second" cols="3">
        <input
          step="0.01"
          style="max-width:100%"
          type="range"
          :value="volume"
          :min="min"
          :max="max"
          @input="handleChange"
        />
      </v-col>
    </v-row>
    <audio
      v-if="currentVideo"
      src="https://r3---sn-p5h-jhor.googlevideo.com/videoplayback?expire=1602902474&ei=agWKX6bxNpGAp-oPu4Cy0A8&ip=196.65.71.149&id=o-AN1zOcLqxUDYxoVhyCiSkn6GSsIv7GgIJwsy0eTl0Pd4&itag=251&source=youtube&requiressl=yes&mh=YM&mm=31%2C29&mn=sn-p5h-jhor%2Csn-aigl6ned&ms=au%2Crdu&mv=m&mvi=3&pl=21&initcwndbps=267500&vprv=1&mime=audio%2Fwebm&gir=yes&clen=3519929&dur=257.501&lmt=1601644384394948&mt=1602880725&fvip=3&keepalive=yes&fexp=23915654&c=WEB&txp=6311222&sparams=expire%2Cei%2Cip%2Cid%2Citag%2Csource%2Crequiressl%2Cvprv%2Cmime%2Cgir%2Cclen%2Cdur%2Clmt&sig=AOq0QJ8wRQIhAMhawhZur6IAW7xevUYzf18Ak9Vvh3qw-8QcyIQvaI1IAiA6on8fWEA4SFuXO26Vrmqj5xfSyerCOvAAAVrd4naZnQ%3D%3D&lsparams=mh%2Cmm%2Cmn%2Cms%2Cmv%2Cmvi%2Cpl%2Cinitcwndbps&lsig=AG3C_xAwRgIhAKIYVPTXNvciH920SiEmr6ov2IRCrUtbSqtgeoR9TzyDAiEAq854KDH7vch33l92V1pnqnyjYEt6mTo45XouNUtop0s%3D&ratebypass=yes"
      autoplay
    ></audio>
  </div>
</template>

<script>
export default {
  props: ['currentVideo'],
  data() {
    return {
      volume: 0.5,
      min: 0,
      max: 1,
    };
  },
  methods: {
    handleChange(event) {
      this.volume = event.target.value;
    },
  },
};
</script>

<style scoped lang="scss">
.controls {
  text-align: center;

  .first {
    .v-btn {
      margin-right: 15px;
    }
  }

  .second {
    display: flex;
    justify-content: center !important;
    align-items: center !important;
  }
}
.song-info {
  text-align: center;
  width: 100%;

  h1 {
    font-size: 1em;
    font-weight: 500;
    max-width: 75%;
    margin: auto;
    margin-bottom: 5px;
  }

  p {
    font-size: 0.75em;
    color: #ad1d45;
    text-transform: uppercase;
    font-weight: bold;
  }
}
.direction {
  flex-direction: column;
  position: relative;

  .timings {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: absolute;
    bottom: 10px;
    font-size: 0.75em;

    .color {
      color: #ad1d45;
    }
  }
}
.main-player {
  width: 100%;
  height: 70vh;
}
.avatar-container {
  border: 5px solid rgb(31, 29, 29);
  box-shadow: 0 0 12px 10px #ad1d45;
}
</style>
