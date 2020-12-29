<template>
  <div id="app">
    <div class="container">
      <div class="window">
        <div>
          <div class="window-header">
          <h1 class="title">Customize Your Master's Degree</h1>
          <div class="instructions">Please select <b>3 certificates</b> to see the potential Master's programs that are available to you</div>
        </div>
        <div class="window-body">
          <label class="cell"
                v-for="(cert,idx) in allPossibleCerts" :key="idx"
                :class="{ disabled: selectedThree && !checkIfSelected(cert.name), selected: checkIfSelected(cert.name) }">
            <!-- <div v-if="cert.requiresCompsci">
              Computer Science background required
            </div> -->
            <input type="checkbox" class="visually-hidden"
                  :id="cert.name"
                  :value="cert.name" 
                  v-model="checkedCerts">
            <h4 :for="cert.name">{{ cert.name }}</h4>
          </label>
        </div>
        </div>
        <div class="window-sidebar">
          <div class="certificates-list">
            <h4>Currently Selected Certificates ({{ numOfSelectedCerts }})</h4>
            <ol id="certificates-list">
              <li v-for="cert in checkedCerts" :key="cert.name">
                {{ cert }}
              </li>
            </ol>
          </div>
          <div class="masters-list">
            <h4>Possible Master's Degrees</h4>
            <!-- <div class="placeholder" v-if="numOfSelectedCerts < 3">Please select <b>{{ 3 - numOfSelectedCerts }}</b> more certificates to see your results</div> will need to pluralize -->
            <ul v-if="selectedThree">
              <li><input type="checkbox" id="masters1"> <label for="masters1">Masters of Computer Science</label></li>
              <li><input type="checkbox" id="masters2"> <label for="masters2">Masters of Data Science</label></li>
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
        { name: "Example 1", requiresCompsci: true},
        { name: "Example 2", requiresCompsci: true},
        { name: "Frontend Development", requiresCompsci: true },
        { name: "Cybersecurity", requiresCompsci: true  },
        { name: "Software Architecture", requiresCompsci: true },
        { name: "Foundations of Data Science", requiresCompsci: true},
        { name: "Artifical Intelligence", requiresCompsci: true},
        // { name: "Example 6", requiresCompsci: true},
        // { name: "Advanced Computer Science", requiresCompsci: true},
        // { name: "Geology", requiresCompsci: false},
        // { name: "Example 8", requiresCompsci: false },
        // { name: "Psychology", requiresCompsci: false },
        // { name: "Psychology of Darth Vader", requiresCompsci: false },
        // { name: "Natural Language Processing", requiresCompsci: true },
        // { name: "George W. Bush", requiresCompsci: true},
        // { name: "Filmmaking", requiresCompsci: true},
        // { name: "Music and Technology", requiresCompsci: true},
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
  padding: 1%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.window {
  width: 100%;
  height:100%;
  display: grid;
  grid-template-columns: 3fr 1fr;
  background-color: #fff;
  border: 2px solid $light-grey;
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

  .window-sidebar {
    border-left: 2px solid $light-grey;
    padding: 4%;
    display: grid;
    grid-template-rows: 1fr 2fr;
    // justify-content: space-between;
    .certificates-list {

    }

    .masters-list {

    }

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

  width: 250px;
  height: 90px;

  // .ribbon {
  //   background: $blue;
  //   color: white;
  //   border-radius: 3px 0px 0px 3px; // top-left top-right bottom-right bottom-left
  //   font-size: 0.7rem;
  //   padding: 2px 5px;
  //   position: absolute;
  //   top: 2px;
  //   right: 0px;
  // }
  

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

.instructions {
  font-size: 1.25rem;
}
</style>
