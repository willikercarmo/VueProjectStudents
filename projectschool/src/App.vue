<template>
  <div id="app">
    <Navbar />
    <div class="marginMain">
      <!-- <Students /> -->
      <!-- <Professors /> -->
      <About />
    </div>
  </div>
</template>

<script>
// import Students from "./components/Student/Students";
// import Professors from "./components/Professor/Professors";
import About from "./components/About/About.vue";
import Navbar from "./components/_nav/Navbar";

export default {
  name: "App",
  components: {
    // Students,
    // Professors,
    About,
    Navbar,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");
body {
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}
body,
html {
  margin: 0;
  height: 100%;
}
.marginMain {
  width: 50%;
  margin: auto;
}
#app {
  width: 100%;
}

.btn_danger {
  background-color: #fa4430;
}

.btn {
  padding: 10px 20px;
  cursor: pointer;
  color: white;
  font-weight: bold;
  border: 1px solid #000;
  border-radius: 5px;
  border-bottom: 3px solid black;
}
.btn:hover {
  text-shadow: 1px 1px 1px black;
  border-bottom: 2px solid black;
  margin-top: 3px;
}

table {
  margin: 0px;
  padding: 0px;
  list-style-type: none;
  width: 100%;
}
table tr td {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
}
table thead th {
  background-color: rgb(184, 208, 216) !important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}
.colPequeno {
  width: 5%;
}
</style>
