<template>
  <div id="app">
    
    <div class="container">
      <SearchBar @termChange="oneTermChange"></SearchBar>
      <div class="row">
          <VideoDetail :video="video"></VideoDetail>
      
          <VideoList :videos="videos"  @videoSelect="onVideoSelect"></VideoList>
      </div>
      
     
     
    </div>
   
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
const API_KEY = 'AIzaSyBDM7Cj8wCdzN38O6mfXCzUfGjnFhwrYdY';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail,

  },
  data(){
    return  {
      video: '',
      videos: '',
    }
  },
  methods: {
    oneTermChange (searchTerm) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then( res => {
        this.videos = res.data.items;
        console.log(res);
      });
    },
    onVideoSelect(video){
      this.video = video;
    }
  }
}
</script>

<style>

</style>
