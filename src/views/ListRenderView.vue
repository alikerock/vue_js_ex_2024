<script setup>
import { ref } from 'vue';
const langs = ref(
  [
    {
      parentLangs: 'front',
      items:[
        {lang:'HTML'},
        {lang:'CSS'}
      ]
    },
    {
      parentLangs: 'back',
      items:[
        {lang:'node.js'},
        {lang:'python'}
      ]
    }      
  ]
);

</script>
<template>
  <div class="content">
    <h1>리스트 렌더링</h1>
    <ul>
      <li v-for="(item, value, idx) in langs" :key="idx">
        {{  item }} -  {{  value }} -    {{  idx }}
      </li>
    </ul>
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
