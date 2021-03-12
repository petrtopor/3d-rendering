<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <label for="gl">oбщая длина</label>
    <input type="number" name="gl" v-model="generalLength">
    <input v-model="generalLength" type="range" min="1" max="20">

    <label for="gw">oбщая ширина</label>
    <input type="number" name="gw" v-model="generalWidth">
    <input v-model="generalWidth" type="range" min="1" max="20">

    <label for="ph">высота параллелепипедов</label>
    <input type="number" name="ph" v-model="parallelepipedHeight">
    <input v-model="parallelepipedHeight" type="range" min="1" max="4">

    <label for="pd">габарит параллелепипедов</label>
    <input type="number" name="pd" v-model="parallelepipedDimension">
    <input v-model="parallelepipedDimension" type="range" min="1" max="4">

    <vgl-renderer class="getting-started" camera="camera" scene="scene">
      <vgl-box-geometry name="box" :width="parallelepipedDimension" :height="1" :depth="parallelepipedDimension"></vgl-box-geometry>
      <vgl-scene name="scene">
        <vgl-mesh geometry="box" :position="`-${generalWidth/2}, 0, -${generalLength/2}`"></vgl-mesh>
        <vgl-mesh geometry="box" :position="`${generalWidth/2}, 0, -${generalLength/2}`"></vgl-mesh>
        <vgl-mesh geometry="box" :position="`-${generalWidth/2}, 0, ${generalLength/2}`"></vgl-mesh>
        <vgl-mesh geometry="box" :position="`${generalWidth/2}, 0, ${generalLength/2}`"></vgl-mesh>
      </vgl-scene>
      <vgl-orthographic-camera name="camera" orbit-position="10 0 0" :zoom="20" />
    </vgl-renderer>
  </div>
</template>

<script>
import { VglRenderer, VglScene, VglOrthographicCamera, VglBoxGeometry , VglMesh } from "vue-gl";
export default {
  name: "HelloWorld",
  components: {
    VglRenderer,
    VglScene,
    VglOrthographicCamera,
    VglBoxGeometry,
    VglMesh
  },
  props: {
    msg: String
  },
  data() {
    return {
      generalLength: 20,
      generalWidth: 20,
      parallelepipedHeight: 1,
      parallelepipedDimension: 1
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.getting-started {
  height: 420px;
  width: 420px;
}
</style>
