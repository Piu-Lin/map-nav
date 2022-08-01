<template>
  <div @click="snedAssignMessage(voice)" class="text">声音</div>
  <Interaction/>
</template>

<script setup>
import Interaction from './components/Interaction.vue';
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