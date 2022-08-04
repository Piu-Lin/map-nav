<template>
  <ConnectWechats/>
  <Connect3dCat @trigger="trigger" />
  <Home ref="homeRef"/>
</template>
<script setup>
import ConnectWechats from "./components/connectWechats.vue"
import Connect3dCat from "./components/connect3dcat.vue"
import Home from "./pages/home/home.vue"
import { ref, reactive } from "vue"

/** ue传出的消息转化为对象 */
let uemeg = reactive({})

/** 资源加载是否完成 */
let LoadComplete = ref(false)

/** 初始化home节点 */
let homeRef = ref(null)

// 对ue消息进行转化分类处理
const trigger = (meg) => {
  try{uemeg = JSON.parse(meg)}
  catch(e) {console.log("json格式出错")}
  console.log("已接受的传出消息", uemeg)
  if (uemeg.eventname == "Event_Connected") {
    LoadComplete.value = true
  } else if (uemeg.eventname == "Event_show_target_info"){
    homeRef.value.handleTagetInfoMsg(uemeg)
  } else {
    console.log("未知类型传出消息")
  }
}

</script>
<style>
</style>
