<template>

  <div id='mainDiv'>
    
    <div id='nonViewDataContainer'>
    </div>
    
    <div id='titleBanner'>
      <img id="logo" style="cursor:pointer;" @click="goToCurriculum()" src="circleLOGO.png" alt="">
      <span id="nameOfWorksheet">Extension 4: Create Sentences</span>
      <p id="themeName" @click="backToSelector()">{{ this.theme }}   {{ this.unit }}</p>
    </div>

    <div id="dataAndImageContainer">   
        <div id='actualImageContainer'>
        <img id="bigImage" src="circleLOGO.png" alt="">
      </div>  
        <div id="studentInputContainer">
            <p class='sentenceInfo' id="abSentenceInfo">Click an image below and then write your own sentence. Click to hear your work.</p>
            <input class="practiceInput" id="practiceInput1" type="text" maxlength="100">
            <div class='soundPlayImage' id="soundPlayImage1" @click="playSound()"> > </div>
        </div>
    </div>

    <div id="horizontalLine"></div>

    <div class='imagesContainer'>
      <div v-for="(product, index) in products" :key="product._id">
        <div v-if="product.theme == theme">
          <div v-if="product.unit == unit">
            <div class="imageAndWordContainer">
              <img class='smallImage' :id=index  @click="makeImageBig(index)" :src="product.photo" alt="">

              <br>
              <span class='smallImageTitle'>{{ product.vocabulary }}</span>
          </div>
          </div>
        </div>  
      </div>

    </div>
  </div>
    
</template>

<script>

export default {
  
  async asyncData({ $axios }) {
    try {
      let response = await $axios.$get("http://localhost:3000/api/products");
      // console.log(response.products);
      return {
        products: response.products
      }
    } catch (err) {
    }
  },
  data() {

    let params = this.$route.query;
    let theme = params.theme;
    let unit = params.unit;
    const titleee = theme.charAt(0).toUpperCase() + theme.slice(1) + " " + unit;
    return {
      title: titleee,
      unit: unit,
      theme: theme,
      recorder: null,
    }
  },
  created () {
    const title = this.title;
    if (title) {
      try {
        document.title = title
      } catch {
        // console.log("")
      }
    }
  },
  methods: {
  getTitle (vm) {
    const { title } = vm.$options
    if (title) {
      return typeof title === 'function'
        ? title.call(vm)
        : title
    }
  },
    playSound(){
      let studentInput = document.getElementById("practiceInput1");
      let speech = new SpeechSynthesisUtterance();      
      speech.text = studentInput.value;
      window.speechSynthesis.speak(speech);
      console.log('soundPLayed');
    },
    makeImageBig(index) {

      let bigImage = document.getElementById("bigImage");
      let littleImageSource = document.getElementById(index).src;
      bigImage.src = littleImageSource;

      let practice1 = document.getElementById("practiceInput1");
      practice1.value = "";
    },

    goToCurriculum() {
      window.open ('curriculum4','_self',false)
    },
    
    getInfo(){
        return this.theme;
    },
    backToSelector(){
      window.open ('workSelector?theme=' + this.theme + '&unit=' + this.unit,'_self',false)
    },
  },

};

</script>

<style>

/* @import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap'); */

body {
  background-color: lightcyan;
  /* font-family: 'Lato', sans-serif; */
}

#nameOfWorksheet {
    grid-column: 2;
    justify-self: stretch;
    text-align: center;
    font-size: 2rem;
    text-transform: capitalize;
    white-space: pre;
    background-color: lavender;
    margin: auto;
    padding: 5px;
    border-radius: 10px;
    border: 1px solid rgb(2, 124, 53); 
    transform: scale(0.9);
    cursor: pointer;
}

.imageAndWordContainer > span {
  padding-left: 5%;
  font-size: 0.7em;
  text-align: center;
}


#abSentenceInfo {
  margin-top: 20px;
  margin-left: 10px;
  margin-bottom: 10px;
  font-size: 1.3em;
}

#bcSentenceInfo {
  margin-top: 20px;
  margin-left: 10px;
  margin-bottom: 10px;
}

#studentInputContainer {
    display: flex;
    flex-direction: column;
    
    margin: auto;
    margin-top: 10px;
    width: 800px;
    height: 120px;
    background-color: lavender;
    border: 8px solid salmon;
    border-radius: 10px;
}


.practiceInput {
    height: 2.5em;
    width: 713px;
    font-size: 1.4em;
    margin: 10px;
}

input[type=text] {
  border-radius: 10px;
  outline: none;
}

#titleBanner {
    display: grid;
    grid-template-columns: 90px 4fr 3fr;
    align-items: center; 
    visibility: visible;
    background-color: salmon;
    border-bottom: 2px solid rgb(1, 58, 1);
}

#themeName {
    grid-column: 3;
    justify-self: stretch;
    text-align: center;
    font-size: 2rem;
    text-transform: capitalize;
    white-space: pre;
    background-color: lavender;
    margin: auto;
    padding: 5px;
    border-radius: 10px;
    border: 1px solid rgb(2, 124, 53); 
    transform: scale(0.9);
    cursor: pointer;
}

.smallImage {
  object-fit: cover;
  padding: 3px;
  height: 80px;
  width: 110px;
  border: 1px solid rgb(1, 58, 1);
  border-radius: 5px;
  margin: 3px;
}

.smallImage:hover {
  background:  salmon;
  color: black;
  cursor: pointer;
}

.smallImage:focus {
  background: darkgreen;
  border-color: lightsalmon;
  color: black;
  cursor: pointer;
}

#imageAndWordContainer {
  display: flex;
  justify-content: space-evenly;
}

.soundPlayImage {
  font-size: 2.5rem;
  color: white;
  background-color: rgb(2, 124, 53);
  border-radius: 35%;
  padding-left: 3px;
  padding-right: 3px;
  border: 3px solid black;
  width: 54px;
  height: 54px;
  text-align: center;
}

#soundPlayImage1 {
  position: relative;
  top: -60px;
  left: 727px;
}

@keyframes buttonStuff {
  0% {background-color: rgb(2, 124, 53);}
  100% {background-color: lightsalmon;}
}

@keyframes afterStuff {
  0% {opacity: 0;background-color: rgb(2, 124, 53);}
  100% {opacity: 1;background-color:lightsalmon;}
}

.soundPlayImage:hover {
  cursor: pointer;
  animation: buttonStuff 375ms forwards;
  color: black;
}

.soundPlayImage:hover::after {
  position: absolute;
  opacity: 0;
  top: 8px;
  left: 65px;
  content: "play";
  background-color: lightsalmon;
  font-size: 1rem;
  width: 80px;
  border: 3px solid black;
  border-left: 1px solid black;
  border-right: 4px solid black;
  padding: 5px;
  border-radius: 5px;
  border-top-left-radius: 50%;
  border-bottom-left-radius: 50%;
  animation: afterStuff 375ms forwards;
  z-index: 888888;
}

#horizontalLine {
  width: auto;
  height: 30px;
  background-color: salmon;
  border-top: 4px solid darkgreen;
  margin-top: 20px;
}

#actualImageContainer {
  display: flex;
  align-items: center;
  justify-items: center;
  margin: auto;
  border: 8px solid salmon;
  border-radius: 10px;
  background-color: salmon;
}

#actualImageContainer > img {
  align-self:center;
  justify-self: center;
}

#logo {
  height: 40px;
  transform: translateX(15px) translateY(-1px);
  border-radius: 10px;
}

#textContainer {
  display: block;
  margin: 5px;
}

#replaceableText1 {
  margin: auto;
  width: 500px;
  min-height: 400px;
  margin-top: 10px;
  padding: 5px;
  background-color: rgb(0, 87, 36);
  color: white;
  font-size: 1.5em;
  border: 10px solid salmon;
  border-radius: 5px;
}

#dataAndImageContainer {
  display: flex;
  flex-direction: column;
  align-content: center;
}
#actualImageContainer {
    margin-top: 10px;
}

#bigImage {
  object-fit: cover;
  height: 410px;
  border-radius: 5px;
}

.imagesContainer {
  display: flex;
  align-content: space-around;
  margin: auto;
  padding-top: 10px;
}

.imagesContainer > div {
  flex-basis: auto;
}

#nonViewDataContainer {
  display: none;
}

span {
  white-space: pre;
}

hr {
  width: 95%; 
  margin-left: 10px;
}

</style>