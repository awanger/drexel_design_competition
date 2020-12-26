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
               :class="{ disabled: selectedThree && !checkIfSelected(cert.name), selected: checkIfSelected(cert.name) }">
          <div v-if="cert.requiresCompsci" class="ribbon">
            Computer Science background required
          </div>
          <input type="checkbox" class="visually-hidden"
                 :id="cert.name"
                 :value="cert.name" 
                 v-model="checkedCerts">
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
          <div class="placeholder" v-if="numOfSelectedCerts < 3">Please select <b>{{ 3 - numOfSelectedCerts }}</b> more certificates to see your results</div> <!-- will need to pluralize -->
          <ul v-if="selectedThree" id="masters-list">
            <li>Masters 1</li>
            <li>Masters 2</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data() { 
    return {
      allPossibleCerts: [
        { name:"HCI/UX", requiresCompsci: false },
        { name: "Information Systems", requiresCompsci: false},
        { name: "Computer Science Foundations", requiresCompsci: false },
        { name: "Technology Leadership", requiresCompsci: false },
        { name: "Frontend Development", requiresCompsci: true },
        { name: "Cybersecurity", requiresCompsci: true  },
        { name: "Software Architecture", requiresCompsci: true },
        { name: "Foundations of Data Science", requiresCompsci: true},
        { name: "Artifical Intelligence / Machine Learning", requiresCompsci: true},
        { name: "Advanced Computer Science", requiresCompsci: true},
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
$blue: #232d38;
$yellow: #ffc600;

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  color: $blue;
}

.container {
  max-width: 100vw;
  height: 90vh;
  padding: 2%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.window {
  width: 100%;
  height:100%;
  display: grid;
  grid-template-rows: 1fr 6fr 3fr; // pancake stack layout
  background-color: #fff;
  border: 2px solid $light-grey;
  border-radius: 10px;
  padding-top: 10px;
  .window-header {
    text-align: center;
  }

  .window-body {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1rem;
    margin: 2%;
    user-select: none;
  }

  .window-footer {
    border-top: 1px solid $light-grey;
    padding: 1% 8%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
}

.disabled {
  opacity: 0.3;
  pointer-events: none;
}

.cell {
  border: 1px solid $light-grey;
  border-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;

  .ribbon {
    background: $blue;
    color: white;
    border-radius: 3px 0px 0px 3px; // top-left top-right bottom-right bottom-left
    font-size: 0.75rem;
    padding: 2px 5px;
    position: absolute;
    top: 2px;
    right: 0px;
  }

  &:hover {
    background-color: lighten($light-grey, 24%);
    cursor: pointer;
  }
  &.selected {
    background-color: $yellow;
  }
}

.visually-hidden {
  appearance: none;
  position: absolute; 
  left: -100vw;
  width: 0;
  height: 0;
}
</style>
