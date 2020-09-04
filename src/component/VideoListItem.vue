<template>
  <li class="media list-group-item" @click="onVideoSelect">
    <img class="mr-3" :src="thumnailUrl" :alt="title" />
    <div class="media-body">{{ title }}</div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  computed: {
    title() {
      return this.video.snippet.title
    },
    thumnailUrl() {
      return this.video.snippet.thumbnails.default.url
    },
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video)
    },
  },
}
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}

li:hover {
  background-color: #eee;
}
</style>