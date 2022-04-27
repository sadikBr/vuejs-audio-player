<template>
  <div class="favorites">
    <SongsList
      groupName="My Favorite Songs"
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
.favorites {
  width: 100%;
  height: 100%;
  padding: 12px;
}
</style>
