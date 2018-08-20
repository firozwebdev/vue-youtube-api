<template>
  <div>
    <ul  class="list-group col-md-4">
       <VideoListItem v-for="video in videos" :video="video" :key="video.etag" @videoSelect="onVideoSelect"></VideoListItem>
    </ul>
  </div>
</template>

<script>

import VideoListItem  from './VideoListItem';
export default {
  name: 'VideoList',
  props: ['videos'],
  components: {
    VideoListItem
  },
  methods: {
   onVideoSelect(video){
      this.$emit('videoSelect',video);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
