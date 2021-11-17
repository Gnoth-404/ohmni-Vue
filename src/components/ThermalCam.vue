<template>
  <div class="camera">
    <div class="name">{{ title }}</div>
    <!-- Begin of Root Component -->
    <video class="feed"></video>
    <button class="snap"> SNAP </button>
    <!-- End of Root Component -->
  </div>
</template>

<script>
export default {
  name: "ThermalCam",
  props: {
    title: String
  }
}
</script>

<style scoped>
.camera {
  margin: 0;
  padding: 0;
}
.name {
  margin: 0;
  border-radius: 3px;
  padding: 10px;
  width: 100%;
  font-size: 30px;
  color: white;
}
.feed {
  height: 450px;
  width: 800px;
}
</style>