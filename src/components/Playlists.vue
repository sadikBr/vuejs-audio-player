<template>
  <v-item-group multiple>
    <h1 class="group-title">My Playlists</h1>
    <v-row class="cards-container">
      <v-col class="d-inline-block dimension" cols="12">
        <v-row justify="center">
          <v-dialog v-model="dialog" persistent max-width="600px">
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                class="create-btn"
                width="150px"
                height="150px"
                v-bind="attrs"
                v-on="on"
                fab
                dark
              >
                <v-icon dark>mdi-plus</v-icon>
              </v-btn>
            </template>
            <v-card>
              <v-card-title>
                <span class="headline">Create New Playlist</span>
              </v-card-title>
              <v-card-text>
                <v-container>
                  <v-row>
                    <v-col cols="12">
                      <v-text-field
                        label="Playlist Name*"
                        type="text"
                        required
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12">
                      <v-text-field
                        label="Playlist Background Image"
                        type="text"
                      ></v-text-field>
                    </v-col>
                  </v-row>
                </v-container>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn text @click="dialog = false">Close</v-btn>
                <v-btn text @click="dialog = false">Save</v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </v-row>

        <v-card-title>
          Create Playlist
        </v-card-title>
      </v-col>

      <v-col class="d-inline-block dimension" v-for="n in 4" :key="n" cols="12">
        <v-btn height="150px" width="150px" fab to="/playlist">
          <v-img
            class="round-images"
            src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
            height="150px"
            width="150px"
          ></v-img>
        </v-btn>

        <v-card-title>
          Playlist Name
        </v-card-title>
      </v-col>
    </v-row>
  </v-item-group>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
    };
  },
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
div.v-card__title {
  display: block;
  text-align: center !important;
  font-size: 0.8em;
  font-weight: normal;
  line-height: 1rem;
}
.create-btn {
  display: block;
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;
}
.dimension {
  width: 200px !important;
  text-align: center center;

  .v-btn {
    display: block;
    margin: auto;
  }
}
.round-images {
  border-radius: 50%;
}
</style>
