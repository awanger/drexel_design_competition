<template>
  <div id="app">
    <div class="container">
    <div class="window">
      <div class="window-header">
        <h1 class="title">Mix and Match</h1>
        <div class="instructions">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Debitis, perferendis.</div>
      </div>
      <div class="window-body">
        <label class="cell"
               v-for="(cert,idx) in allPossibleCerts" :key="idx"
               :class="{ disable: selectedThree && !checkIfSelected(cert.name), selected: checkIfSelected(cert.name) }">
          <input type="checkbox" class="visually-hidden"
                 :id="cert.name"
                 :value="cert.name" 
                 v-model="checkedCerts" :disabled="selectedThree && !checkIfSelected(cert.name)">
          <h4 :for="cert.name">{{ cert.name }}</h4>
        </label>
      </div>
      <div class="window-footer">
        <div class="certificates">
          <h3>Currently Selected Certificates ({{ numOfSelectedCerts }})</h3>
          <ol id="certificates-list">
            <li v-for="cert in checkedCerts" :key="cert.name">
              {{ cert }}
            </li>
          </ol>
        </div>
        <div class="masters">
          <h3>Possible Master's Degrees</h3>
          <div class="placeholder" v-if="numOfSelectedCerts < 3">Please select <b>{{ 3 - numOfSelectedCerts }}</b> more certificates to see results</div> <!-- will need to pluralize -->
          <ul v-if="selectedThree" id="masters-list">
            <li>Masters 1</li>
            <li>Masters 2</li>
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
      allPossibleCerts: [
        { name:"HCI/UX" },
        { name: "Information Systems"},
        { name: "Computer Science Foundations"},
        { name: "Technology Leadership"},
        { name: "Frontend Development"},
        { name: "Cybersecurity" },
        { name: "Software Architecture"},
        { name: "Foundations of Data Science"},
        { name: "Artifical Intelligence / Machine Learning"},
        { name: "Advanced Computer Science"},
      ],
      checkedCerts: []
    }
  },
  methods: {
    checkIfSelected: function(cert) {
      return this.checkedCerts.includes(cert);
    }
  },
  computed: {
    numOfSelectedCerts: function() {
      return this.checkedCerts.length;
    },
    selectedThree: function() {
      return this.numOfSelectedCerts === 3;
    }
  }
}
</script>

<style lang="scss">
$light-grey: #b7b7b5;

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
  width: 1100px;
  height:700px;
  display: grid;
  grid-template-rows: auto 1fr auto;
  background-color: #fff;
  border: 1px solid $light-grey;
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
    border-top: 1px solid $light-grey;
    padding: 3% 8%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
}

.disable {
  color: $light-grey;
}

// temporary class
.cell {
  border: 1px solid;
  &:hover {
    background-color: $light-grey;
    cursor: pointer;
  }
  &.selected {
    background-color: skyblue;
  }
}

.visually-hidden {
  appearance: none;
  position: absolute; 
  left: -100vw;
  width: 0;
  height: 0;
}

.placeholder {
  // background-color: $light-grey;
}
</style>
