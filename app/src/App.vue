<script setup>

import { ref } from 'vue'

import HelloWorld from './components/HelloWorld.vue'
import Posts from './components/Posts.vue'
import PostsId from './components/PostsId.vue'
import UserId from './components/UserId.vue'
import Users from './components/Users.vue'

</script>

<script>

export default {
  data(){
    return {
      post_id: 1,
      user_id: 5
    }
  },

  methods: {
    setPostId(dados) {
      this.user_id = dados
      console.log(dados)
    }
  }
}

</script>

<template>

  <div class="container">

    
    <Posts />
    <PostsId />
    <Users />
    
    <Users @botaoClicado="setPostId" />
    <UserId v-bind:num="user_id" />

  </div>


</template>

<style scoped>

</style>
