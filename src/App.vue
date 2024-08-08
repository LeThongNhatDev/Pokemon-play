<script setup>
import { ref } from 'vue';
import main_start from './components/main_start.vue';
import screen_game from './components/screen_game.vue';
import result from './components/result.vue';
const check_setting = ref('default');
const cards = ref([])
const cardsGamePlay = ref([])
 const total_number_game = ref([]);
 const array_one = ref([]);
 const array_two = ref([]);
const startAt = ref(null)
const timer = ref(0);

 function shuffle(mang) {
  for (let i = mang.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [mang[i], mang[j]] = [mang[j], mang[i]];
  }
  return mang; // Thêm dòng này để trả về mảng đã xáo trộn
}


 const clickStart = (total_number)=>{
   total_number_game.value = total_number
  //  array_one.value = Array.from({ length: total_number_game.value / 2 }, (_, i) => i + 1);
  for (let i = 0; i < total_number_game.value / 2; i++) {
    array_one.value.push(i + 1);
  }
   array_two.value = [...array_one.value];
   cards.value = [...array_one.value,...array_two.value];
   cardsGamePlay.value = shuffle(shuffle(shuffle(cards.value)))
   startAt.value = new Date().getTime();
   check_setting.value = 'match';
 }
 
 const onGetResult = ()=>{
   timer.value = new Date().getTime() - startAt.value;
   check_setting.value = "result";
 }
  
 const againGameClick = () =>{
  check_setting.value = 'default';
 }
</script>

<template>
    <main_start  @on-start="clickStart($event)" v-if="check_setting === 'default'"/>
    <screen_game v-if="check_setting === 'match'" :msg="cardsGamePlay" @onFinnish="onGetResult"/>
    <result v-if="check_setting === 'result'" :timer="timer" @againGame="againGameClick"/>
</template>

<style scoped>
 body{
  margin: auto;
 }
 
</style>
