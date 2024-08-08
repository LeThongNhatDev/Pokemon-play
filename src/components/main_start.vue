<script setup>
 import { ref } from 'vue'
 const emitStart = defineEmits(  ['onStart'])

 const onStart = (total_number)=>{
    emitStart("onStart",[total_number]);
 }
</script>
<template>
    <div class="screen_start">
        <h1>         TRÒ CHƠI XẾP HÌNH         </h1>
         <h3>Hãy chọn cấp độ cho màn chơi</h3>
         <div class="action-setting">
            <button type="button" class="button"  @click="onStart(16)">
            <div class="button-top">4 x 4 <br>Dễ</div>
            <div class="button-bottom"></div>
            <div class="button-base"></div>
            </button>
            <button type="button" class="button"  @click="onStart(36)">
            <div class="button-top"> 6 x 6 <br> Cơ bản </div>
            <div class="button-bottom"></div>
            <div class="button-base"></div>
            </button>
            <button type="button" class="button"  @click="onStart(64)">
            <div class="button-top">8 x 8 <br> Khó</div>
            <div class="button-bottom"></div>
            <div class="button-base"></div>
            </button>
           
        
         </div>
        
    </div>
</template>
<style scoped>
.screen_start{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 1rem;
    
}
.action-setting{
    display: flex;
    gap: 2rem;
}
.button {
  -webkit-appearance: none;
  appearance: none;
  position: relative;
  border-width: 0;
  padding: 0 8px 12px;
  min-width: 10em;
  box-sizing: border-box;
  background: transparent;
  font: inherit;
  cursor: pointer;
}

.button-top {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 0;
  padding: 8px 16px;
  transform: translateY(0);
  text-align: center;
  color: #fff;
  text-shadow: 0 -1px rgba(0, 0, 0, .25);
  transition-property: transform;
  transition-duration: .2s;
  -webkit-user-select: none;
  user-select: none;
}

.button:active .button-top {
  transform: translateY(6px);
}

.button-top::after {
  content: '';
  position: absolute;
  z-index: -1;
  border-radius: 4px;
  width: 100%;
  height: 100%;
  box-sizing: content-box;
  background-image: radial-gradient(#cd3f64, #9d3656);
  text-align: center;
  color: #fff;
  box-shadow: inset 0 0 0px 1px rgba(255, 255, 255, .2), 0 1px 2px 1px rgba(255, 255, 255, .2);
  transition-property: border-radius, padding, width, transform;
  transition-duration: .2s;
}

.button:active .button-top::after {
  border-radius: 6px;
  padding: 0 2px;
}

.button-bottom {
  position: absolute;
  z-index: -1;
  bottom: 4px;
  left: 4px;
  border-radius: 8px / 16px 16px 8px 8px;
  padding-top: 6px;
  width: calc(100% - 8px);
  height: calc(100% - 10px);
  box-sizing: content-box;
  background-color: #803;
  background-image: radial-gradient(4px 8px at 4px calc(100% - 8px), rgba(255, 255, 255, .25), transparent), radial-gradient(4px 8px at calc(100% - 4px) calc(100% - 8px), rgba(255, 255, 255, .25), transparent), radial-gradient(16px at -4px 0, white, transparent), radial-gradient(16px at calc(100% + 4px) 0, white, transparent);
  box-shadow: 0px 2px 3px 0px rgba(0, 0, 0, 0.5), inset 0 -1px 3px 3px rgba(0, 0, 0, .4);
  transition-property: border-radius, padding-top;
  transition-duration: .2s;
}

.button:active .button-bottom {
  border-radius: 10px 10px 8px 8px / 8px;
  padding-top: 0;
}

.button-base {
  position: absolute;
  z-index: -2;
  top: 4px;
  left: 0;
  border-radius: 12px;
  width: 100%;
  height: calc(100% - 4px);
  background-color: rgba(0, 0, 0, .15);
  box-shadow: 0 1px 1px 0 rgba(255, 255, 255, .75), inset 0 2px 2px rgba(0, 0, 0, .25);
}

</style>