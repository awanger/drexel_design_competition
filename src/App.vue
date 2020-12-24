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
          <input type="checkbox" id="HCI" value="HCI" v-model="checkedCerts">
          <label for="HCI">HCI/UX</label>
        </div>
        <div class="box">
          <input type="checkbox" id="info" value="info" v-model="checkedCerts">
          <label for="info">Information Systems Certificate</label>
        </div>
        <div class="box">
          <input type="checkbox" id="csf" value="csf" v-model="checkedCerts">
          <label for="csf">Computer Science Foundations</label>
        </div>
        <div class="box">
          <input type="checkbox" id="technology" value="technology" v-model="checkedCerts">
          <label for="technology">Technology Leadership*</label>
        </div>
        <div class="box">
          <input type="checkbox" id="frontend" value="frontend" v-model="checkedCerts">
          <label for="frontend">Frontend Development*</label>
        </div>
        <div class="box">
          <input type="checkbox" id="cybersecurity" value="cybersecurity" v-model="checkedCerts">
          <label for="cybersecurity">Cybersecurity*</label>
        </div>
        <div class="box">
          <input type="checkbox" id="software" value="SoftwareArch" v-model="checkedCerts">
          <label for="software">Software Architecture</label>
        </div>
        <div class="box">
          <input type="checkbox" id="random" value="random" v-model="checkedCerts">
          <label for="random">Random Certificate</label>
        </div>
      </div>
      <div class="window-footer">
        <div class="certificates">
          Currently Selected Certificates
          <ul id="certificates-list">
            <li v-for="cert in checkedCerts" :key="cert">
              {{ cert }}
            </li>
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
  },
  data() { 
    return {
      checkedCerts: []
    }
  }
}
</script>

<style lang="scss">
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

.window {
  width: 800px;
  height:700px;
  display: grid;
  grid-template-rows: auto 1fr auto;
  background-color: #fff;
  border: 1px solid black;
  .window-header {
    text-align: center;
  }

  .window-body {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    margin: 4%;
    user-select: none;
  }

  .window-footer {
    border-top: 1px solid red;
    padding: 3% 8%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
}
// temporary class
.box {
  border: 1px solid;
}
</style>
