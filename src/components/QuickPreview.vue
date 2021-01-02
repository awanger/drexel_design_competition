<template>
  <div class="modal">
    <div class="quick-preview">
      <div class="container">
        <h1 class="header">Artificial Intelligence and Machine Learning</h1>
        <div class="quick-preview-body">
          <h3 class="heading">What do you learn?</h3>
          <p>The four-course curriculum provides fundamental, interdisciplinary education in of a range of artificial intelligence and machine learning topics</p>
          <h3 class="heading">Who is it good for?</h3>
          <p>This program is designed for recent graduates and professionals who are interested in building on their existing quantitative skills to become leaders in the field of artificial intelligence and machine learning.</p>
          <h3 class="heading">What degrees does this pair well with?</h3>
          <p>The program may serve as an entry point to Master of Science degrees in Computer Science, Data Science, and Artificial Intelligence & Machine Learning.</p>
          <h3 class="heading">Is there a pathway of study for students without a strong background in computer science?</h3>
          <p>Our suite of computing programs is designed to support multiple pathways to success. For those without a strong undergraduate background in computing, our Computer Science Foundations Certificate can serve as an introduction and entry point to the AI and Machine Learning program.</p>
        </div>
        <div class="btn-container">
          <div class="btn">Add to Plan</div>
          <div class="btn btn-clear">See Full Certificate Information</div>
        </div>
      </div>
    </div>
</div>
</template>

<script>
export default {
  name: 'QuickPreview',
  props: {
    isOpen: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

  p {
    font-size: 1.1rem;
  }

  .modal {
    display: none;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 5;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0,0,0,0.4); /* Black w/ opacity */

    &.is-visible {
      display: flex;
      justify-content: center;
      align-items: center;
      // maybe disable scrolling
    }
    .quick-preview {
      background-color: white;
      width: 80%;
    }
  }



  .container {
    padding: 2%;
  }

  .header, .heading {
    font-family: Futura;

  }

  .header {
    margin-bottom: 30px;
  }

  .heading {
    text-transform: uppercase;
  }

.btn-container {
  display: grid;
  place-items: center;
  width: 100%;
  height: 75%; // depends on the size of the 

  .btn {
    font-family: Futura;
    padding: 0.35em 1.2em;
    border: 0.1em solid black;
    color: white;
    background-color: black;
    text-decoration:none;
    cursor: pointer;
    text-transform: uppercase;

    display: flex;
    justify-content: center;
    align-items: center;
    width: 20%;
    height: 50px;
    margin-bottom: 1em;

    &.btn-clear {
      background-color: white;
      color: black;
      text-align: center;
    }
  }
}


  
</style>
