<template>
    <div class="container">
        <div>{{targetId}}</div>  
        <div>{{tagetInfo[targetId]}}</div>  
        

        <div @click="handlecloseinfo()" class="back">返回</div> 
    </div>
</template>
<script setup>
import tagetInfo from "./tagetInfo.json"

const emit = defineEmits(["closeInfo"])

const props = defineProps({
    targetId:{type: String,},
});

console.log(props.targetId)

console.log(tagetInfo[props.targetId])



function handlecloseinfo(){
    launch.getConnection().emitUIInteraction('{"eventname": "Event_close_info"}').then(result=>emit("closeInfo"))
}
</script>
<style lang="less" scoped>
.container{
    width: 20%;
    height: 50%;
    position: absolute;
    background-color: yellow;
    z-index: 1;
    .back{
        width: 50px;
        height: 50px;
        background-color:green;
    }
}

</style>