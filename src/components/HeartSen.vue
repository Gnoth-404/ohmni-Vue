<template>
  <div class="sensor">
    <!-- Begin of Root Component -->
    <div class="name">{{ title }}</div>
    <div class="bpm"><i class='bx bxs-heart'></i> <b id="heart"></b> <b>BPM</b></div>
    <button v-on:click = sendCmd()>Click Me</button>
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
    title: String,
    show: String
  },
  data: () => {
    return {
      product: "hit",
      ros: null,
      connected: false,
      //Ros topic
      heart: String,
      bpm: String,
      createCmdVel: String,
      twist: String
    }
  },
  methods: {
    sendCmd() {
      this.createCmdVel = new ROSLIB.Topic({
        ros: this.ros,
        name: "/cmd_vel",
        messageType: "std_msgs/String"
      });

      this.twist = new ROSLIB.Message({
        data: "Button Click Registered"
      });

      this.createCmdVel.publish(this.twist);
      console.log("Published Success")
    },

    listenHeart() {
      this.heartsen = new ROSLIB.Topic({
        ros: this.ros,
        name: "/cmd_vel",
        messageType: "std_msgs/String"
      });

      this.heartsen.subscribe( bpm => {console.log(bpm.data); document.getElementById("heart").innerHTML= bpm.data})
    }
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
    this.listenHeart();
  },
}
</script>
<style scoped>
.name {
  margin: 20px;
  padding: 10px;
  width: 95vw;
  font-size: 30px;
  border-radius: 12px;
  background: #414141;
  color: lightgray;
}
.bpm {
  font-size: 30px;
  color: darkgray;
}
</style>