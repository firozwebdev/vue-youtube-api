<template>
  <div>
    <li  class="list-group-item">
       <img :src="video.snippet.thumbnails.default.url" alt="">
      {{ video.snippet.title }}
      </li>
  </div>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  methods: {
   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
