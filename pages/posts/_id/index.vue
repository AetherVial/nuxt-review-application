<template>
  <div class="container">
    <h1>{{post.title}}</h1>
    <pre>{{post.body}}</pre>
    <nuxt-link to="/posts">Back</nuxt-link>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      post: ''
    }
  },
  async asyncData(context) {
    let {data} = await axios.get(`https://jsonplaceholder.typicode.com/posts/${context.params.id}`)
    return {post: data}
  },
  head() {
    return {
      title: this.post.title
    }
  }
}
</script>