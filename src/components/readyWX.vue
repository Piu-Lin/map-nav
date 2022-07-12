<template>
</template>

<script setup>
const url=window.location.url;
console.log(url);
let vxconf={}
const requestOptions = {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({id:9,url})
}; 

fetch("http://metagis.cc/prod-api/ToolController/getSignature", requestOptions )
  .then(response => response.json())
  .then(data=>
    wx.config({
    debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印。
    appId: data.appId, // 必填，公众号的唯一标识
    timestamp: data.timestamp, // 必填，生成签名的时间戳
    nonceStr: data.nonce, // 必填，生成签名的随机串
    signature: data.signature,// 必填，签名
    jsApiList: ["openLocation"] // 必填，需要使用的JS接口列表
    })
  )
  .then(()=>{
    wx.ready(function(){
    alert("流程结束")
    });
    wx.error(function(res){
    alert("vx坏了",res)
    }); 
  })
 
</script>

<style>

</style>