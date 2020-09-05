<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <!-- v-bind similar to ":" -->
      <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './component/SearchBar'
import VideoList from './component/VideoList'
import VideoDetail from './component/VideoDetail'

const API_KEY = 'AIzaSyBkyPNIqULMgAt45adbl-afrnKQlcBJF9o'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: [],
      selectedVideo: null,
    }
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video
    },
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
