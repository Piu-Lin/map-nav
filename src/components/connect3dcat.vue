<template>
</template>
<script setup>
import { Launcher } from 'live-cat'
import privacy from  "../../private/index.json"
const address = 'https://app.3dcat.live'
// const emit = defineEmits(["trigger"])
const bootstrap = async () => {
  try {
    const launch = new Launcher({
      baseOptions: {
        address,
        appKey:privacy.catAppKeyt,
        startType: 1, //	1:普通链接 | 3:投屏链接
      },
    });
    const player = document.querySelector("body");
    document.querySelector("body").style.width = "100vw";
    document.querySelector("body").style.height = "100vh";
    await launch.automata(player);
    const connection = launch.getConnection()
    const livePlayer = launch.getPlayer()
    window.launch = launch
    window.connection = connection
    window.livePlayer = livePlayer
  } catch (error) {
    console.error(error);
  }
};
window.addEventListener('DOMContentLoaded', () => {
  if (
    navigator.userAgent.includes('miniProgram') ||
    navigator.userAgent.includes('MicroMessenger')
  ) {
    //微信浏览器/微信小程序环境
    document.addEventListener('WeixinJSBridgeReady', bootstrap, false)
  } else {
    bootstrap()
  }
})
</script>
<style>
</style>