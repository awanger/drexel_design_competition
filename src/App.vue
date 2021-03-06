<template>
  <div id="app">
    <div class="container">
      <quick-preview></quick-preview>
      <h1 class="title">Customize Your Master's Degree</h1>
      <div class="window">
        <div class="window-body">
          <input class="search-bar" type="text" placeholder="Search for a certificate..." name="search">
          <div class="card"
                v-for="(cert,idx) in allPossibleCerts" :key="idx"
                :class="{ disabled: selectedThree && !checkIfSelected(cert.name), selected: checkIfSelected(cert.name) }">

            <img :src="getImgPath(cert.imgFile)" alt="image goes here">
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
            <h1 class="certificates-window-header">My Degree Plan</h1>
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
import QuickPreview from './components/QuickPreview.vue';


export default {
  name: 'App',
  components: {
    QuickPreview
  },
  data() { 
    return {
      allPossibleCerts: [
        { name:"HCI/UX", requiresCompsci: false, imgFile: 'ux.jpeg' },
        { name: "Information Systems", requiresCompsci: false, imgFile: 'FED.jpeg'},
        { name: "Comp Sci Foundations", requiresCompsci: false, imgFile: 'CSF.jpeg' },
        { name: "Technology Leadership", requiresCompsci: false, imgFile: 'TL.jpeg' },
        { name: "Frontend Development", requiresCompsci: true, imgFile: 'FED.jpeg' },
        { name: "Cybersecurity", requiresCompsci: true, imgFile: 'Cyber.jpeg'},
        { name: "Software Architecture", requiresCompsci: true, imgFile: 'SA.jpeg'},
        { name: "Foundations of Data Science", requiresCompsci: true, imgFile: "DS.jpeg"},
        { name: "Artifical Intelligence", requiresCompsci: true, imgFile: 'psy.jpeg'},
        { name: "Artifical Intelligence", requiresCompsci: true, imgFile: 'psy.jpeg'},
        { name: "Artifical Intelligence", requiresCompsci: true, imgFile: 'psy.jpeg'},
        { name: "Artifical Intelligence", requiresCompsci: true, imgFile: 'psy.jpeg'},
        { name: "Artifical Intelligence", requiresCompsci: true, imgFile: 'psy.jpeg'},
      ],
      checkedCerts: [],
    }
  },
  methods: {
    checkIfSelected: function(cert) {
      return this.checkedCerts.includes(cert);
    },
    getImgPath: function(imgFileName) {
      return imgFileName ? require(`./assets/images/${imgFileName}`) : '';
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

<style lang="scss" scoped>
$light-grey: #b7b7b5;
$blue: #232d38;
$yellow: #ffc600;
$overlay-color: lighten(#FFFDFD, 10%);

@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

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
  position: sticky;
  top: 17vh;

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

  overflow: hidden;

  img {
    object-fit: cover;
    max-width: 300px;
  }

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
    // background-color: $yellow;
  }
}

.btn-container {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  width: 100%;
  height: 75%; // depends on the size of the

  .btn {
    @include flex-center;
    padding: 0.35em 1.2em;
    border: 0.1em solid $blue;
    color:$blue;
    text-decoration:none;
    cursor: pointer;

    width: 75%;
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
