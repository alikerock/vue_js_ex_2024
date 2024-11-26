<script setup>
import { ref, watch } from 'vue'

const question = ref('')
const answer = ref('질문에는 보통 물음표가 포함됩니다. ;-)')
const loading = ref(false)
watch(question, async(newQestion, oldQuestion)=>{
  if(newQestion.includes('?')){
    loading.value=true;
    answer.value = '생각중...';
    try{
      const res = await fetch('https://yesno.wtf/api')
      answer.value =  (await res.json()).answer === 'yes' ?'네':'아니오'
    } catch (error){
        this.answer =  '에러!' +error
    }
  }
})
</script>

<template>
  <div class="content">
    <h1>감시자</h1>
    <!-- <input type="text" @input="event=>question=event.target.value"> -->
    <input type="text" v-model="question">
    <p>{{ answer }}</p>
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
