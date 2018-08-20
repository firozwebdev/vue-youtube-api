<template>
  <div id="app">
    
    <SearchBar @termChange="oneTermChange"></SearchBar>
    
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
const API_KEY = 'AIzaSyBDM7Cj8wCdzN38O6mfXCzUfGjnFhwrYdY';
export default {
  name: 'App',
  components: {
    SearchBar
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
      }).then( res => console.log(res));
    }
  }
}
</script>

<style>

</style>
