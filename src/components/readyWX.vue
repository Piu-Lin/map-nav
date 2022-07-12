<template>
</template>

<script setup>
const url=window.location.href;
const requestOptions = {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({id:9,url})
}; 
fetch("http://metagis.cc/prod-api/ToolController/getSignature", requestOptions )
  .then(response => response.json())
  .then(data=>{
    wx.config({
        debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印。
        appId: data.appId, // 必填，公众号的唯一标识
        timestamp: data.timestamp, // 必填，生成签名的时间戳
        nonceStr: data.nonce, // 必填，生成签名的随机串
        signature: data.signature,// 必填，签名
        jsApiList: ["openLocation"] // 必填，需要使用的JS接口列表
    })
  }
  )
  .then(()=>{
    wx.ready(function(){
    alert("流程结束")
    wx.openLocation({
    latitude: 30.1726, // 纬度，浮点数，范围为90 ~ -90
    longitude: 120.1, // 经度，浮点数，范围为180 ~ -180。
    name: '位置', // 位置名
    address: '测试地址', // 地址详情说明
    scale: 1, // 地图缩放级别,整型值,范围从1~28。默认为最大
    infoUrl: 'https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html' // 在查看位置界面底部显示的超链接,可点击跳转
    });
    });
    wx.error(function(res){
        alert("网络异常，请检查",res)
    }); 
  })
 
</script>

<style>

</style>