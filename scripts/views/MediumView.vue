<template>
  <news-list :posts="posts"></news-list>
</template>

<script>
import NewsList from './../components/NewsList.vue'
import {fetchMediumPosts} from './../apis/medium-api'

export default {
  name: 'medium-view',
  components: {
    NewsList
  },
  data () {
      return {
          posts: []
      }
  },
  created () {
    this.fetchData()
  },
  watch: {
    // call again the method if the route changes
    '$route': 'fetchData'
  },
  methods: {
    fetchData () {
      this.posts = []
      fetchMediumPosts(this.loadPosts)
    },
    loadPosts (result) {
      this.posts = result
    }
  }
}
</script>
