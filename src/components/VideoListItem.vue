<template>
  <div>
    <li  class="list-group-item media" @click="onVideoSelect">
       <img class="mr-3" :src="thumbnailUrl" alt="">
       <div class="media-body">
          {{ video.snippet.title }}
       </div>
     
      </li>
  </div>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  computed: {
    thumbnailUrl(){
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect(){
      this.$emit('videoSelect',this.video);
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    li {
      display: flex;
    }
    li:hover{
      background: #eee;
      cursor:pointer;
    }
</style>
