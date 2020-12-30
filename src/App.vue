<template>
  <div id="app">
    <div class="container">
      <h1 class="title">Customize Your Master's Degree</h1>
      <div class="window">
        <div class="window-body">
          <input class="search-bar" type="text" placeholder="Search for a certificate..." name="search">
          <div class="card"
                v-for="(cert,idx) in allPossibleCerts" :key="idx"
                :class="{ disabled: selectedThree && !checkIfSelected(cert.name), selected: checkIfSelected(cert.name) }">
            <div class="overlay">
              <div class="btn-container">
                <div class="btn">View Details</div>
                <label class="btn" :for="cert.name">
                  <span v-if="!checkIfSelected(cert.name)">Add to Plan</span>
                  <span v-else class="added">Remove from Plan</span>
                  <input type="checkbox" class="visually-hidden" :id="cert.name" :value="cert.name" v-model="checkedCerts">
                </label>
              </div>
            </div>
            <footer class="card-footer">
              <h4 :for="cert.name">{{ cert.name }}</h4>
            </footer>
          </div>
        </div>
        <div class="window-sidebar">
          <div class="certificates-window">
            <h4>My Plan</h4>
            <ol>
              <li class="placeholder">{{ checkedCerts[0] }}</li>
              <li class="placeholder">{{ checkedCerts[1] }}</li>
              <li class="placeholder">{{ checkedCerts[2] }}</li>
            </ol>
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
$overlay-color: lighten(#FFFDFD, 10%);

#app {
  font-family: Georgia, 'Times New Roman', Times, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $blue;
}

.container {
  max-width: 100vw;
  height: 90vh;
  padding: 2%;
}

.title {
  font-family: Futura;
  font-size: 3em;
  text-align: center;
}

.window {
  width: 100%;
  height:100%;
  display: grid;
  grid-template-columns: 4fr 2fr;
  background-color: #fff;
  // border: 2px solid $light-grey;
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

  }
}


.search-bar {
  grid-column: 1/4;
  padding: 10px;
  font-size: 1em;
  border: 1px solid $light-grey;
}


.certificates-window {
  border: 2px solid $light-grey;
  padding: 4%;

  .placeholder {
    width: 100%;
    height: 35px;
    border: 2px solid $light-grey;
    margin-bottom: 1rem;
  }
}

.masters-list {

}

.disabled {
  opacity: 0.3;
  pointer-events: none;
}

.card {
  border: 1px solid $light-grey;
  position: relative;
  aspect-ratio: 1/1; // only works in Chrome Canary
  height: 280px;

  display: grid;
  grid-template-rows: 1fr 1fr;

  .card-footer {
    position: absolute;
    background-color: white;
    z-index: 3;
    width: 100%;
    text-align: center;
    bottom: 0;
    border-top: 1px solid $light-grey;
  }

  .overlay {
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: $overlay-color;
    opacity: 0; // temporarily make this 1
    transition: 0.3s;

    &:hover {
      opacity: 1;
    }
  }

  
  &.selected {
    background-color: $yellow;
  }
}

.btn-container {
  display: grid;
  place-items: center;
  width: 100%;
  height: 75%; // depends on the size of the 

  .btn {
    padding: 0.35em 1.2em;
    border: 0.1em solid $blue;
    color:$blue;
    text-decoration:none;
    cursor: pointer;

    display: flex;
    justify-content: center;
    align-items: center;
    width: 80%;
    height: 50px;

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
