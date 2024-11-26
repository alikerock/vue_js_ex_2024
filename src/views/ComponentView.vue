<script setup>
import { ref } from 'vue';
import ButtonCounter from './ButtonCounter.vue';
import BlogPost from './BlogPost.vue';

const posts = ref([
  {id:1, title:'title1'},
  {id:2, title:'title2'},
  {id:3, title:'title3'}
])

const fontsize = ref(1);

</script>
<template>
  <div class="content">
    <h1>컴포넌트</h1>
    <ButtonCounter/>
    <ButtonCounter/>
    <ButtonCounter/>
    <hr>
    <div :style="{fontSize:fontsize+'em'}">
      <BlogPost 
        v-for="post in posts" 
        :key="post.id" 
        :title="post.title"
        @enlarge-text="fontsize+=0.1"
        @smaller-text="fontsize-=0.1"
      />
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .content {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
