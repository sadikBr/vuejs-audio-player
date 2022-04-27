<template>
  <div class="mymusic">
    <ContentGroup title="Recently Played" />
    <Playlists />
  </div>
</template>

<script>
import ContentGroup from '../components/ContentGroup';
import Playlists from '../components/Playlists';

export default {
  components: {
    ContentGroup,
    Playlists,
  },
};
</script>

<style scoped>
.mymusic {
  width: 100%;
  height: 100%;
  padding: 12px;
}
</style>
