<script setup>
  import { reactive, computed } from 'vue';

  const author = reactive({
    name:'홍길동',
    books:[
      'Vue 1 - Vue Basic',
      'Vue 2 - Vue Guide',
      'Vue 3 - Vue Advanced'
    ]
  })
  const myfunc = computed(()=>{
    return author.books.length > 0 ? '있어요' : '없어요'
  })
</script>

<template>
  <div class="content">
    <h1>계산된 속성</h1>
    <p>책이 있습니까?</p>
    <span>{{ myfunc }}</span>
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
