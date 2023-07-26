<script setup>

import {computed, reactive} from "vue";

const properties = reactive(
    {
      perspective: 100,
      rotateX: 0,
      rotateY:0,
      rotateZ:0
    }
)

const box = computed(()=>{
  return {
    transform: `perspective(${properties.perspective}px)
     rotateX(${properties.rotateX}deg)
      rotateY(${properties.rotateY}deg)
       rotateZ(${properties.rotateZ}deg)`
  }
})

</script>

<template>
  <section class="playground">
    <div class="input-area">
      <label>perspective: {{properties.perspective}} px</label>
      <input type="range" min="0" max="999" v-model="properties.perspective">

      <label>rotateX: {{properties.rotateX}} deg</label>
      <input type="range" min="0" max="90"  v-model="properties.rotateX">

      <label>rotateY: {{properties.rotateY}} deg</label>
      <input type="range" min="0" max="90" v-model="properties.rotateY">
      <label>rotateZ: {{properties.rotateZ}} deg</label>
      <input type="range" min="0" max="90" v-model="properties.rotateZ">

      <button type="button">Reset</button>
    </div>

    <div class="output-area">
      <div class="box" :style="box">
      </div>
    </div>
  </section>

</template>

<style scoped>

.playground{
  display: flex;
place-items: center;
  gap: 5rem;
}

.input-area {
  display: flex;
  flex-direction: column;
  text-align: left;
  gap: 10px;
}

.output-area {
  border: 1px solid cornflowerblue;
  width: 200px;
  height: 200px;
  display: flex;
  place-items: center;


}

.box {

  background-color: #535bf2;
  width: 150px;
  height: 150px;
  margin: auto;
}

</style>
