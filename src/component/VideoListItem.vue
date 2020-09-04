<template>
  <li class="list-group-item">
    <img :src="thumnailUrl" :alt="title" />
    {{ title }}
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
}
</script>