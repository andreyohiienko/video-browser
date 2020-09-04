<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './component/SearchBar'
const API_KEY = 'AIzaSyBeJzzQ9emIyILEhWGUcBfvSzxyzhTgNvQ'

export default {
  name: 'App',
  components: {
    SearchBar,
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get('https://googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm,
          },
        })
        .then((response) => console.log(response))
    },
  },
}
</script>
