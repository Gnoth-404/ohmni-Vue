<template>
  <div id="dash">
      <!-- Begin of Root Component -->
      <div class="toolbar">
        <a class="tools_start"><i class='bx bxl-vuejs'><span> {{title}}</span></i></a>
        <a href="#" class="tools"><i class='bx bxs-cctv' ></i>
          <div class="tooltip" >
            <span > Thermal Camera </span>
          </div>
        </a>
        <a href="#" class="tools"><i class='bx bxs-heart' ></i></a>
        <a href="#" class="tools"><i class='bx bx-line-chart' ></i></a>
        <a href="#" class="tools_end"><i class='bx bxs-log-out' id="log_out"></i></a>
      </div>
    <section class="home-section">
      <div class="text">Dashboard</div>
    </section>
    <!-- End of Root Component -->
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  props: {
    title: String
  }
}
</script>

<style scoped>
/* Google Font Link */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap');

#dash {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  }
.toolbar{
  position: fixed;
  top: 0;
  right: 0;
  width: 100%;
  height: 70px;
  display: grid;
  grid-template-columns: 3fr 1fr 1fr 1fr 3fr;
  align-content: center;
  font-size: 30px;
  background: #11101D;
}
a{
  color: aliceblue;
  min-width: 100px;
}
.toolbar .tools_start{
  padding-left: 5%;
  text-align: left;
}
.toolbar .tools_end{
  position: relative;
  right: 0;
  padding-right: 5%;
  text-align: right;
}
.toolbar .tools{
  text-align: center;
  border-bottom-left-radius: 12px;
  border-bottom-right-radius: 12px;
  transition: all 0.2s ease;
}
.toolbar .tools:hover{
  color: black;
  background: white;
}
.toolbar .tools_end{
  color: white;
  border-radius: 2px;
}
.toolbar .tools_end #log_out{
  padding: 8px;
  position: relative;
  color: white;
  border-radius: 2px;
  background: #11101D;
  border: 1px solid red;
  transition: all 0.2s ease;
}
.toolbar .tools_end #log_out:hover{
  padding: 10px;
  position: relative;
  color: white;
  border-radius: 2px;
  background: red;

}
.tooltip {
  font-size: 20px;
  position: absolute;
  padding: 10px;
  margin-top: 25px;
  min-width: 10%;
  opacity: 0;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  background: white;
  z-index: 1;
  border-radius: 12px;
}
.toolbar .tools:hover .tooltip{
  opacity: 1;
}

</style>