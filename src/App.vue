<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <!-- v-bind similar to ":" -->
    <VideoList :videos="videos"></VideoList>
    {{ videos.length }}
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './component/SearchBar'
import VideoList from './component/VideoList'
const API_KEY = 'AIzaSyBeJzzQ9emIyILEhWGUcBfvSzxyzhTgNvQ'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
  },
  data() {
    return {
      videos: [],
    }
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm,
          },
        })
        .then((response) => {
          this.videos = response.data.items
        })
    },
  },
}
</script>
