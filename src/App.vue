<template>
  <div id="app">
    
    <SearchBar @termChange="oneTermChange"></SearchBar>
    <VideoList :videos= videos></VideoList>
   
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
const API_KEY = 'AIzaSyBDM7Cj8wCdzN38O6mfXCzUfGjnFhwrYdY';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList

  },
  data(){
    return  {
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
    }
  }
}
</script>

<style>

</style>
