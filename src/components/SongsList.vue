<template>
  <v-list class="ma-auto pb-0" max-width="950px" subheader>
    <v-subheader>{{ groupName }}</v-subheader>

    <v-list-item
      class="border"
      v-for="song in songs"
      :key="song.id.videoId"
      link
    >
      <v-list-item-avatar width="65px" height="65px">
        <v-img :src="song.snippet.thumbnails.medium.url"></v-img>
      </v-list-item-avatar>
      <v-list-item-content>
        <v-list-item-content>
          <v-list-item-title v-text="song.snippet.title"></v-list-item-title>
          <v-list-item-title
            class="font"
            v-text="song.snippet.channelTitle"
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
          :to="{ name: 'Play', params: { id: song.id.videoId } }"
        >
          <v-icon>mdi-play</v-icon>
        </v-btn>
      </v-list-item-icon>
    </v-list-item>
  </v-list>
</template>

<script>
export default {
  props: ['songs', 'groupName'],
};
</script>

<style scoped>
.border {
  border-bottom: 1px solid rgb(122, 120, 120);
  margin-bottom: 4px;
}
.btn-edit {
  margin: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.v-list-item__icon {
  align-self: center !important;
}
.font {
  font-size: 0.7em;
  font-weight: normal;
  margin-top: 5px;
  color: rgb(230, 78, 103);
}
</style>
