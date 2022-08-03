<template>
  <Interaction/>
  <ShowTargetInfo @closeInfo="closeInfo" v-if="showTarget" :targetId="targetId"  />
</template>

<script setup>
import Interaction from './components/Interaction.vue';
import ShowTargetInfo from './components/ShowTagetInfo.vue'
import { ref, reactive } from "vue"

/** 所要展示的对应点位 */
let targetId= ref("")

/** 是否显示细节弹窗 */
let showTarget = ref(false)

// 处理显示详情事件
function handleTagetInfoMsg(uemeg){
  targetId.value=uemeg.type
  showTarget.value=true
  console.log("主页收到",targetId.value)
}

const closeInfo = ()=>{
  showTarget.value = false
}

// 交出方法
defineExpose({
  handleTagetInfoMsg,
});

</script>

<style>
.text{
    width: 200px;
    height: 200px;
    position: absolute;
    z-index: 10;
    background-color:red;
    right: 20px;
}
</style>