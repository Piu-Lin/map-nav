<template>
<div class="container">
    <div @click="snedAssignMessage(touristRoutesList)" class="box">旅游路线清单</div>
    <div @click="snedAssignMessage(touristRoutes1)" class="box">打开旅游路线</div>
    <div @click="snedAssignMessage(viewPointList1)" class="box">显示点位清单</div>
    <div @click="snedAssignMessage(closeInfo)" class="box">关闭点位信息</div>
    <div @click="snedAssignMessage(resetDefaultView)" class="box">重置位置</div>

</div>

</template>


<script setup>
import {ref,reactive } from 'vue'

const touristRoutesList='{"eventname": "Event_tourist_routes_list"}'
const touristRoutes1='{"eventname": "Event_tourist_routes","type":"rout_001"}'
const touristRoutes2='{"eventname": "Event_tourist_routes","type":"rout_002"}'

const viewPointList1='{"eventname": "Event_view_point_list","type":"list_001"}'
const viewPointList2='{"eventname": "Event_view_point_list","type":"list_002"}'
const viewPointList3='{"eventname": "Event_view_point_list","type":"list_003"}'
const viewPointList4='{"eventname": "Event_view_point_list","type":"list_004"}'

const closeInfo='{"eventname": "Event_close_info"}'
const resetDefaultView='{"eventname": "Event_reset_default_view"}'

function snedAssignMessage(assignMessage) {
    console.log("开始传输"+assignMessage)
    launch.getConnection().emitUIInteraction(assignMessage).then(result=>console.log(result))
    console.log("传输结束")
}
</script>


<style lang="less" scoped>
.container{
    z-index: 1;
    width:70%;
    height:10%;
    position: absolute;
    left:50%;
    top:80%;
    transform: translate(-50%,-50%);
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    .box{
        width:15%;
        height:100%;
        background-color:blue;
        border-radius:8px;
    }
}
</style>