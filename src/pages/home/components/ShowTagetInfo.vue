<template>
    <div class="container">
        <div>{{targetId}}</div>  
        <div id="infotitle">{{tagetInfo[targetId][0]}}</div>
        <img id="infopic" src="/src/assets/tagetInfo/pic/pic.jpg" alt="">
        <div id="infocontent">{{tagetInfo[targetId][0]}}</div>
        <div class="botton-box">
            <div @click="handlevoices(true)" class="back">播放声音</div> 
            <div @click="handlevoices(false)" class="back">停止播放</div> 
        </div>
        <div class="botton-box">
            <div @click="handlecloseinfo()" class="back">返回</div> 
            <div @click="handlenaviga()" class="back">导航</div> 
        </div>
        <audio ref="myaudio" src="/src/assets/tagetInfo/voice/Endings.mp3" id="myaudio" controls="controls" loop="false" hidden="true"></audio>
    </div>
</template>
<script setup>
import tagetInfo from "./tagetInfo.json"
import showLocation from "/src/tools/showLocation.js"

const emit = defineEmits(["closeInfo"])

const props = defineProps({
    targetId:{type: String,},
});

function handlecloseinfo(){
    launch.getConnection().emitUIInteraction('{"eventname": "Event_close_info"}').then(result=>emit("closeInfo"))
}

function handlevoices(flg){
    if (flg){
        console.log("开始播放")
        console.log(myaudio)
        myaudio.play()
        
    } else {
        console.log("停止播放")
        myaudio.pause();
        myaudio.load();
    }
}

function handlenaviga(){
    console.log("导航")
    showLocation(120,30,"测试位置","测试说明")
}

</script>
<style lang="less" scoped>
.container{
    width: 20%;
    height: 70%;
    position: absolute;
    background-color: yellow;
    z-index: 1;
    #infopic{
        width: 70%;
        height: 50%;
    }
    .botton-box{
        display:flex;
        width: 100%;
        justify-content: space-between;
    .back{
            width: 45%;
            bottom: 5px;
            height: 20px;
            background-color:green;
        }       
    }
    
}

</style>