<script setup>
import { ref } from 'vue';
import ButtonCounter from './ButtonCounter.vue';
import BlogPost from './BlogPost.vue';
import tab1 from './tabs/tab1.vue';
import tab2 from './tabs/tab2.vue';
import tab3 from './tabs/tab3.vue';

const posts = ref([
  {id:1, title:'title1'},
  {id:2, title:'title2'},
  {id:3, title:'title3'}
])
const tabsTitle = ref(['tab1','tab2','tab3']);
const tabsCP = ref([tab1,tab2,tab3]);
const fontsize = ref(1);
const currentTab = ref(tabsCP.value[0]);

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
    <hr>
    <h2>tab</h2>
    <button 
      v-for="(title, idx) in tabsTitle" 
      :key="idx"
      @click = "currentTab = tabsCP.value[idx]; console.log(idx)"
    >{{ title }}</button>
    <component :is="currentTab"/>
    
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
