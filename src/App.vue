<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
  </div>
</template>

<script>
import SearchBar from './component/SearchBar'
const API_KEY = 'AIzaSyBeJzzQ9emIyILEhWGUcBfvSzxyzhTgNvQ'

export default {
  name: 'App',
  components: {
    SearchBar,
  },
  methods: {
    onTermChange(searchTerm) {
      console.log(searchTerm)
    },
  },
}
</script>
