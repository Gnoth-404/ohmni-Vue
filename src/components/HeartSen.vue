<template>
  <div class="sensor">
    <!-- Begin of Root Component -->
    <div class="name">{{ title }}</div>
    <div>

    </div>
    <!-- End of Root Component -->
  </div>
</template>

<script>
import ROSLIB from "roslib";

export default {
  name: "HeartSen",
  props: {
    title: String
  },
  data: () => ({
    ros: null,
    connected: false,
  }),
  mounted() {
    // This is ros connection
    this.ros = new ROSLIB.Ros({
      url: "ws://localhost:9090",
    });
    this.ros.on("connection", () => {
      this.connected = true;
    });
    console.log("This ROSLIB connection", this.ros);
  }
}
</script>

<style scoped>
.name {
  border-radius: 3px;
  padding: 10px;
  width: 100%;
  font-size: 30px;
  color: white;
}
</style>