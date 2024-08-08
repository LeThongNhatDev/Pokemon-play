<template>
  <div class="box-card">
    <card v-for="(card,index) in msg" 
    :key="index" 
    :imgbg="card + '.png'" 
    :idCard="{value: card,index: index}"
    @checkCard="checkIdCard($event)" 
    ref="carIndex"
    />

  </div>
</template>
<script setup>
import card from './card.vue';
import { ref } from 'vue';
const carIndex = ref([])
const props = defineProps({
  msg: Array,
})
const rules = ref([]);
const emitTrue = defineEmits(['onFinnish']);
const checkIdCard = (card)=>{
   if(rules.value.length === 2){
    return false;
   }

  rules.value.push(card); 
  if( rules.value.length === 2 && rules.value[0].value === rules.value[1].value){

        carIndex.value[rules.value[0].index].isDisabled();
         carIndex.value[rules.value[1].index].isDisabled();
         rules.value = []; 


         const elementCheck = document.querySelectorAll('.card-disabled');
         if(elementCheck && elementCheck.length === carIndex.value.length -2){
           setTimeout(()=>{
            emitTrue("onFinnish"); 
           },800)
         } 
         
   
  }else if(rules.value.length === 2 && rules.value[0].value !== rules.value[1].value){
        console.log("sai");
        setTimeout(()=>{
          carIndex.value[rules.value[0].index].closeCard();
         carIndex.value[rules.value[1].index].closeCard();
         rules.value = [];
        },800)
       
  }else{
    return false;
  }
  
}

</script>
<style scoped>
.box-card{
  width: 80%;
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
    height: 100%;
    margin: auto;
    
}
</style>