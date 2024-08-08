<template>
        <div class="card" :class="Disabled ? 'card-disabled' : '' ">
        <div class="card-inner" @click="clickFlipped" :class="isFlipped ? 'card-inner-flipped' : '' ">
        <div class="card-front">
        </div>
        <div class="card-back" :style="{ backgroundImage: imgbgprops }">
        </div>
        </div>
        </div>
</template>
<script setup>
 import { ref } from 'vue'
  const isFlipped = ref(false)
  const Disabled = ref(false)
  const props = defineProps({
  imgbg: String,
  idCard:Array,
  });
  const emitCheck = defineEmits(  ['checkCard'] )

  const clickFlipped = () =>{
    if(Disabled.value){
      return false;
    }
    isFlipped.value = !isFlipped.value
     if(isFlipped.value){
      emitCheck("checkCard",props.idCard)
     }
  }
  
  const closeCard = () => {
  isFlipped.value = false;
  };
  const isDisabled = () => {
    Disabled.value = true;
  };
defineExpose({closeCard,isDisabled})
  

const imgbgprops = `url('/src/assets/image/${props.imgbg}')`;
</script>
<style scoped>

.card {
  width: 120px;
  height: 150px;
  perspective: 1000px;
  cursor: pointer;
}

.card-inner {
  width: 100%;
  height: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform 0.999s;
}

.card>.card-inner-flipped {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  background-size: 80px;
  background-repeat: no-repeat;
  background-position: center;
}

.card-front {
    background-image: url("/src/assets/image/icon_back.png");
    background-size: 100px;
    background-repeat: no-repeat;
    background-position: center;
  color: #fff;
  display: flex;
  align-items: center;
  border: 10px solid #6A2C70;
  border-radius: 10px;
  justify-content: center;
  font-size: 24px;
  transform: rotateY(0deg);
}

.card-back {
  background-color: #181818;
  color: #fff;
  display: flex;
  align-items: center;
  border: 10px solid #6A2C70;
  border-radius: 10px;
  justify-content: center;
  font-size: 24px;
  transform: rotateY(180deg);
}
 .card-disabled{
  cursor: default;
 }
</style>