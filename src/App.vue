<template>
  <div id="app">
    <div class="container">
    <div class="window">
      <div class="window-header">
        <h1 class="title">Mix and Match</h1>
        <div class="instructions">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Debitis, perferendis.</div>
      </div>
      <div class="window-body">
        <div class="box">
          <input type="checkbox" id="HCI">
          <label for="HCI">HCI Certificate</label>
        </div>
        <div class="box">
          <input type="checkbox" id="info">
          <label for="info">Information Systems Certificate</label>
        </div>
        <div class="box">
          <input type="checkbox" id="csf">
          <label for="csf">Computer Science Foundations</label>
        </div>
        <div class="box">
          <input type="checkbox" id="technology">
          <label for="technology">Technology Leadership*</label>
        </div>
        <div class="box">
          <input type="checkbox" id="frontend">
          <label for="frontend">Frontend Development*</label>
        </div>
        <div class="box">
          <input type="checkbox" id="cybersecurity">
          <label for="cybersecurity">Cybersecurity*</label>
        </div>
        <div class="box">
          <input type="checkbox" id="software">
          <label for="software">Software Architecture</label>
        </div>
        <div class="box">
          <input type="checkbox" id="random">
          <label for="random">Random Certificate</label>
        </div>
      </div>
      <div class="window-footer">
        <div class="certificates">
          Currently Selected Certificates
          <ul id="certificates-list">
            <li>Certificate 1</li>
            <li>Certificate 2</li>
            <li>Certificate 3</li>
          </ul>
        </div>
        <div class="masters">
          Possible Master's Degrees
          <ul id="masters-list">
            <li>Masters 1</li>
            <li>Masters 2</li>
            <li>Masters 3</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  max-width: 100vw;
  height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
