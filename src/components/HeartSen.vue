<template>
  <div class="sensor">
    <!-- Begin of Root Component -->
    <div class="name">{{ title }}</div>
    <button v-on:click="sendCmd(0.2, 0, 0, 0, 0, 0.0)">Forward</button>
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
    //Ros topic
    listenHeartBeat: String,
    createCmdVel: String,
    twist: String
  }),
  methods: {
    sendCmd(x_linear, y_linear, z_linear, x_angular, y_angular, z_angular) {
      this.createCmdVel = new ROSLIB.Topic({
        ros: this.ros,
        name: "/cmd_vel",
        messageType: "geometry_msgs/Twist",
      });

      this.twist = new ROSLIB.Message({
        linear: {
          x: x_linear,
          y: y_linear,
          z: z_linear,
        },
        angular: {
          x: x_angular,
          y: y_angular,
          z: z_angular,
        },
      });
    },
  },
  mounted() {
    // This is ros connection
    this.ros = new ROSLIB.Ros({
      url: "ws://localhost:9090",
    });
    this.ros.on("connection", () => {
      this.connected = true;
    });
    console.log("This is ROSLIB connection", this.ros);
    this.sendCmd(0.0, 0, 0, 0, 0, 0.0);
  },
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