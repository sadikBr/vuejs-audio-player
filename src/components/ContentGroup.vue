<template>
  <v-item-group multiple>
    <h1 class="group-title">{{ title }}</h1>
    <v-row class="cards-container">
      <v-col
        class="d-inline-block dimensions"
        v-for="item in data"
        :key="item.id"
        cols="12"
        mb="2"
      >
        <v-item>
          <v-card class="mx-auto" dark>
            <v-img
              :src="item.snippet.thumbnails.medium.url"
              height="150px"
            ></v-img>

            <v-row align="center">
              <v-col class="padding" cols="10">
                <v-card-title>
                  {{ item.snippet.title.substr(0, 15) + '...' }}
                </v-card-title>

                <v-card-subtitle>
                  {{ item.snippet.channelTitle }}
                </v-card-subtitle>
              </v-col>
              <v-btn
                dark
                fab
                x-small
                :to="{
                  name: 'Play',
                  params: {
                    id: item.kind.includes('playlist')
                      ? item.snippet.resourceId.videoId
                      : item.id,
                  },
                }"
              >
                <v-icon>mdi-play</v-icon>
              </v-btn>
            </v-row>
          </v-card>
        </v-item>
      </v-col>
    </v-row>
  </v-item-group>
</template>

<script>
export default {
  props: ['title', 'data'],
};
</script>

<style scoped lang="scss">
.group-title {
  font-size: 1.5rem;
  font-weight: normal;
}
.cards-container {
  display: block !important;
  white-space: nowrap !important;
  overflow: auto hidden !important;
}
.dimensions {
  width: 300px !important;
}
.padding {
  padding: 0 12px !important;

  div {
    font-size: 1em !important;

    &:last-child {
      font-size: 0.8em !important;
    }
  }
}
</style>
