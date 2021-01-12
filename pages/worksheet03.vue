<template>

  <div id='mainDiv'>
    
    <div id='nonViewDataContainer'>
    </div>
    
    <div id='titleBanner'>
      <img id="logo" style="cursor:pointer;" @click="goToCurriculum()" src="circleLOGO.png" alt="">
      <span id="nameOfWorksheet">Extension 3: Practice Sentences</span>
      <p id="themeName" @click="backToSelector()">{{ this.theme }}   {{ this.unit }}</p>
    </div>

    <div id="dataAndImageContainer">     
        <div id="studentInputContainer">
            <p class='sentenceInfo' id="abSentenceInfo">Click an image below to begin.</p>
            <input class="practiceInput" id="practiceInput1" type="text" @keydown="checkIfCorrect1()">
            <input class="practiceInput" id="practiceInput2" type="text" @keydown="checkIfCorrect1()">
            <input class="practiceInput" id="practiceInput3" type="text" @keydown="checkIfCorrect1()">
            <span id='partition'></span>
            <p class='sentenceInfo' id="bcSentenceInfo">Click an image below to begin.</p>
            <input class="practiceInput" id="practiceInput4" type="text" @keydown="checkIfCorrect2()">
            <input class="practiceInput" id="practiceInput5" type="text" @keydown="checkIfCorrect2()">
            <input class="practiceInput" id="practiceInput6" type="text" @keydown="checkIfCorrect2()">   
        </div>
      <div id='actualImageContainer'>
        <img id="bigImage" src="circleLOGO.png" alt="">
      </div>
    </div>

    <div class='soundPlayImage' id="soundPlayImage1" @click="playSound1()"> > </div>
    <div class='soundPlayImage' id="soundPlayImage2" @click="playSound2()"> > </div>
    
    
    
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

import $ from 'jquery';

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
        // console.log("document mia")
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
  checkIfCorrect1() {
      $(document).ready(function(){
          let input1 = document.getElementById("practiceInput1");
          let input2 = document.getElementById("practiceInput2");
          let input3 = document.getElementById("practiceInput3");

          let abSentence = document.getElementById("abSentenceInfo");

          if (input1.value == abSentence.textContent) {
              input1.style.backgroundColor = "lightgreen";
          } else {
              input1.style.backgroundColor = "white";
          }

          if (input2.value == abSentence.textContent) {
              input2.style.backgroundColor = "lightgreen";
          } else {
              input2.style.backgroundColor = "white";
          }

          if (input3.value == abSentence.textContent) {
              input3.style.backgroundColor = "lightgreen";
          } else {
              input3.style.backgroundColor = "white";
          }
        });
    },
    checkIfCorrect2() {
        $(document).ready(function(){
            let input1 = document.getElementById("practiceInput4");
            let input2 = document.getElementById("practiceInput5");
            let input3 = document.getElementById("practiceInput6");
            
            let vocab = document.getElementById("bcSentenceInfo");
            
            if (input1.value == vocab.textContent) {
                input1.style.backgroundColor = "lightgreen";
            } else {
                input1.style.backgroundColor = "white";
            }

            if (input2.value == vocab.textContent) {
                input2.style.backgroundColor = "lightgreen";
            } else {
                input2.style.backgroundColor = "white";
            }

            if (input3.value == vocab.textContent) {
                input3.style.backgroundColor = "lightgreen";
            } else {
                input3.style.backgroundColor = "white";
            }
        });
    },

    closeInfo() {
        let infoDisplay = document.getElementById("wordInfoDisplay");
        infoDisplay.style.visibility = "hidden";

        let wordInfoDisplay = document.getElementById("wordInfoDisplay");
        wordInfoDisplay.style = "inherit";
        
        let wordChosen = document.getElementById("wordChosen");
        wordChosen.style = "inherit";

        let studentInput = document.getElementById("studentInput");
        studentInput.style = "inherit";
        
        let teacherWindowCloser = document.getElementById("teacherWindowCloser");
        teacherWindowCloser.style = "inherit";
    },

    
    playSound1(){
      let abSentence = document.getElementById("abSentenceInfo");
      let speech = new SpeechSynthesisUtterance();      
      speech.text = abSentence.innerHTML;
      window.speechSynthesis.speak(speech);
      console.log('soundPLayed');
    },
    playSound2(){
      let bcSentence = document.getElementById("bcSentenceInfo");
      let speech = new SpeechSynthesisUtterance();      
      speech.text = bcSentence.innerHTML;
      window.speechSynthesis.speak(speech);
      console.log('soundPLayed');
    },
    makeImageBig(index) {

      let bigImage = document.getElementById("bigImage");
      let littleImageSource = document.getElementById(index).src;
      bigImage.src = littleImageSource;

      let abSentenceText = document.getElementById("abSentenceInfo");
      console.log("before", abSentenceText);
      abSentenceText.innerText = this.products[index].abSentence;
      console.log("after", abSentenceText);
      abSentenceText.innerHTML = this.products[index].abSentence;
      abSentenceText.style.fontSize = "1.3em";

      let bcSentenceText = document.getElementById("bcSentenceInfo");
      bcSentenceText.innerHTML = this.products[index].bcSentence;
      bcSentenceText.style.fontSize = "0.9em";

      let practice1 = document.getElementById("practiceInput1");
      let practice2 = document.getElementById("practiceInput2");
      let practice3 = document.getElementById("practiceInput3");
      let practice4 = document.getElementById("practiceInput4");
      let practice5 = document.getElementById("practiceInput5");
      let practice6 = document.getElementById("practiceInput6");
      
      practice1.style.backgroundColor = 'white';
      practice2.style.backgroundColor = 'white';
      practice3.style.backgroundColor = 'white';
      practice4.style.backgroundColor = 'white';
      practice5.style.backgroundColor = 'white';
      practice6.style.backgroundColor = 'white';

      practice1.value = "";
      practice2.value = "";
      practice3.value = "";
      practice4.value = "";
      practice5.value = "";
      practice6.value = "";

      practice1.placeholder = this.products[index].abSentence;
      practice4.placeholder = this.products[index].bcSentence;
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

input[type=text] {
  border-radius: 10px;

}

.practiceInput {
    height: 2.5em;
    width: 350px;
    font-size: 1.2em;
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
    margin: 10px;
    min-width: 500px;
    max-width: 500px;
    min-height: 500px;
    max-height: 500px;
    background-color: lavender;
    border: 8px solid salmon;
    border-radius: 10px;
}

.practiceInput {
    height: 2.5em;
    width: 462px;
    font-size: 0.9em;
    margin: 10px;
}

#practiceInput4 {
    font-size: 0.9em;
}

#practiceInput5 {
    font-size: 0.9em;
}

#practiceInput6 {
    font-size: 0.9em;
} 

#partition {
  border: 4px solid salmon
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
  position: absolute;
  top: 73px;
  left: 446px;
}

#soundPlayImage2 {
  position: absolute;
  top: 304px;
  left: 446px;
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

#buttonsContainer {
  display: flex;
  border: 2px solid darkgreen;
  background-color:  salmon;
  margin-top: 20px;
  padding: 10px;
  border-radius: 5px;
}

#buttonsContainer > p {
  margin: auto;
  padding: 2px;
  border: 1px solid black;
  background-color:  rgb(0, 87, 36);
  color: white;
  border-radius: 5px;
}

#buttonsContainer > p:hover {
  background: rgb(250, 195, 189);
  color: black;
  cursor: pointer;
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
  align-content: center;
}

#bigImage {
  max-width: 490px;
  max-height: 410px;
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