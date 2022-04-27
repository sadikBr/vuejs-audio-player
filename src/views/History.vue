<template>
  <div class="history">
    <SongsList
      groupName="Songs History"
      :songName="songName"
      :artistName="artistName"
    />
  </div>
</template>

<script>
import SongsList from '../components/SongsList';

export default {
  components: {
    SongsList,
  },
  data() {
    return {
      songName: 'Song Name Comming From Youtube',
      artistName: 'Artist Name',
    };
  },
};
</script>

<style scoped>
.history {
  width: 100%;
  height: 100%;
  padding: 12px;
}
</style>
