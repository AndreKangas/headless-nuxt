<template>
    <div class="container">
        <h1 class="text-center">{{post.title}}</h1>

        <!-- eslint.disable-next-line vue/no-v-html -->
        <article class="py-" v-html="post.content"></article>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { PostsState } from '~/store/posts'

export default Vue.extend({
    async asyncData({ store, params }) {
    await store.dispatch('posts/getPost', params.slug)
  },
    computed: {
        post() {
            return (this.$store.state.posts as PostsState).post
        },
    },
})
</script>