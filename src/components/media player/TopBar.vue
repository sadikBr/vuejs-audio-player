<template>
  <div class="top-bar">
    <h1>
      <v-app-bar-nav-icon
        class="nav-icon"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      Comming Next
    </h1>
    <v-navigation-drawer
      v-model="drawer"
      width="450px"
      absolute
      bottom
      temporary
    >
      <v-list nav dense>
        <h5 class="title">Up Comming Songs</h5>
        <v-list-item-group>
          <v-list-item
            class="border"
            v-for="video in relatedVideos"
            :key="video.id.videoId"
            link
          >
            <v-list-item-avatar width="45px" height="45px">
              <v-img :src="video.snippet.thumbnails.medium.url"></v-img>
            </v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-content>
                <v-list-item-title
                  v-text="video.snippet.title"
                ></v-list-item-title>
                <v-list-item-title
                  class="font"
                  v-text="video.snippet.channelTitle"
                ></v-list-item-title>
              </v-list-item-content>
            </v-list-item-content>
            <v-list-item-icon>
              <v-btn class="btn-edit" x-small fab>
                <v-icon>mdi-dots-vertical</v-icon>
              </v-btn>
              <v-btn
                class="btn-edit"
                fab
                x-small
                :to="{ name: 'Play', params: { id: video.id.videoId } }"
              >
                <v-icon>mdi-play</v-icon>
              </v-btn>
            </v-list-item-icon>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  props: ['relatedVideos'],
  data() {
    return {
      drawer: false,
      volume: 0.5,
      min: 0,
      max: 1,
      songName: 'The Song Name Here',
      artistName: 'Artist Name',
    };
  },
};
</script>

<style scoped lang="scss">
.border {
  border-bottom: 1px solid rgb(122, 120, 120);
  margin-bottom: 4px;
}
.font {
  font-size: 0.6em !important;
  font-weight: normal;
  margin-top: 5px;
  color: rgb(230, 78, 103);
}
.btn-edit {
  margin: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.top-bar {
  width: 100%;
  height: 10vh;
  padding: 0 10px;
  display: flex;
  align-items: center;

  h1 {
    font-size: 1.2em;
    font-weight: normal;
    display: flex;
    align-items: center;
    flex: 1;

    .nav-icon {
      margin-right: 15px;
    }
  }
}
.title {
  font-size: 0.8em !important;
  font-weight: 400;
  margin-bottom: 8px;
}
</style>
