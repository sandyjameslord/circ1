<template>

  <div id='mainDiv'>
    
    <div id='nonViewDataContainer'>
      <p id="vocabInfo">Click an image below to begin.</p>
      <p id="abSentenceInfo">Click an image below to begin.</p>
      <p id="bcSentenceInfo">Click an image below to begin.</p>
      <p id="abQuestionInfo">Click an image below to begin.</p>
      <p id="bcQuestionInfo">Click an image below to begin.</p>
      <p id="abQuestionDomain">Click on an image.</p>
      <p id="bcQuestionDomain">Click on an image.</p>
    </div>
    
    <div id='titleBanner'>
      <img id="logo" style="cursor:pointer;" @click="goToCurriculum()" src="circleLOGO.png" alt="">
      <span id="nameOfWorksheet">Extension 2: Practice Words</span>
      <p id="themeName" @click="backToSelector()">{{ this.theme }}   {{ this.unit }}</p>
    </div>

    <div id="dataAndImageContainer">  
      <div id='textContainer'>
        <div id="textAndDomainContainer">
            <p class='replaceableText clickable' @click="getWord()" id='replaceableText'>Practice:</p>
            <input class="practiceInput" id="practiceInput1" type="text" @keydown="checkIfCorrect()">
            <input class="practiceInput" id="practiceInput2" type="text" @keydown="checkIfCorrect()">
            <input class="practiceInput" id="practiceInput3" type="text" @keydown="checkIfCorrect()">
            <input class="practiceInput" id="practiceInput4" type="text" @keydown="checkIfCorrect()">
            <input class="practiceInput" id="practiceInput5" type="text" @keydown="checkIfCorrect()">
            <input class="practiceInput" id="practiceInput6" type="text" @keydown="checkIfCorrect()">
        </div>
        
      </div>
      <div id='actualImageContainer'>
        <img id="bigImage" src="circleLOGO.png" alt="">
      </div>
    </div>

    <div class='soundPlayImage' id="soundPlayImage" @click="playSound()"> > </div>
    
    <div id="replaceableDomainText">Domain Info Type</div>
    
    <div id="horizontalLine"></div>

    <div id='wordInfoDisplay'>
      <p id='wordChosenTitle'>You clicked</p>
      <p id='wordChosen'></p>
      <p id='wordPlayTitle'>Listen to your choice</p>
      <p id="wordPracticeTitle">Practice writing: </p>
      <input id='studentInput' type="text" placeholder="Practice writing..." @keydown="checkIfCorrect()">

      <span class='closer' id='teacherWindowCloser' @click="closeInfo()">X</span>
      <div class='soundPlayImage' id="soundPlayImage2" @click="playOneWord()"> > </div>
            
    </div>

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
      checkIfCorrect() {
          $(document).ready(function(){
              let input1 = document.getElementById("practiceInput1");
              let input2 = document.getElementById("practiceInput2");
              let input3 = document.getElementById("practiceInput3");
              let input4 = document.getElementById("practiceInput4");
              let input5 = document.getElementById("practiceInput5");
              let input6 = document.getElementById("practiceInput6");

              let vocab = document.getElementById("vocabInfo");
              let word = document.getElementById("replaceableText");
              
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

              if (input4.value == vocab.textContent) {
                  input4.style.backgroundColor = "lightgreen";
              } else {
                  input4.style.backgroundColor = "white";
              }

              if (input5.value == vocab.textContent) {
                  input5.style.backgroundColor = "lightgreen";
              } else {
                  input5.style.backgroundColor = "white";
              }

              if (input6.value == vocab.textContent) {
                  input6.style.backgroundColor = "lightgreen";
              } else {
                  input6.style.backgroundColor = "white";
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

    getWord() {
      $('#replaceableText').click(function(){
          let studentInput = document.getElementById("studentInput");
          studentInput.value = "";
          studentInput.style.backgroundColor = "white";
          var sel = window.getSelection();
          var str = sel.anchorNode.nodeValue,len = str.length, a = sel.anchorOffset, b = sel.anchorOffset;
          while(str[a]!=' '&&a--){}; if (str[a]==' ') a++;
          while(str[b]!=' '&&b++<len){};   

          let word = str.substring(a,b);
          let punct = [',', '.', '?', '!', ','];
          for (let i = 0; i< punct.length; i++){
          if (word.endsWith(punct[i])) {
              word = word.slice(0, (word.length - 1))
            }
          }
          let infoDisplay = document.getElementById("wordInfoDisplay");
          infoDisplay.style.visibility = "visible";

          let infoWindow = document.getElementById("wordChosen");
          infoWindow.innerText = word;
        });
    },
    playOneWord() {
        let replaceableText = document.getElementById("wordChosen");
        let speech = new SpeechSynthesisUtterance();      
        speech.text = replaceableText.innerHTML;
        window.speechSynthesis.speak(speech);
    },  
    playSound(){
        let replaceableText = document.getElementById("replaceableText");
        let speech = new SpeechSynthesisUtterance();      
        speech.text = replaceableText.innerHTML;
        window.speechSynthesis.speak(speech);
        console.log('soundPLayed');
    },
    makeImageBig(index) {
        let bigImage = document.getElementById("bigImage");
        let littleImageSource = document.getElementById(index).src;
        bigImage.src = littleImageSource;

        let firstText = document.getElementById("replaceableText");
        firstText.innerHTML = "Practice: " + this.products[index].vocabulary;
        firstText.style.fontSize = "1.5rem";
        let vocab = document.getElementById("vocabInfo");
        vocab.innerHTML = this.products[index].vocabulary;

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

        practice1.placeholder = this.products[index].vocabulary + "...";
        practice2.placeholder = this.products[index].vocabulary + "...";
        practice3.placeholder = this.products[index].vocabulary + "...";

        let infoDisplay = document.getElementById("wordInfoDisplay");
        infoDisplay.style.visibility = "hidden";
    
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

#practiceInput1 {
    position: absolute;
    top: 120px;
    left: 23px;
}

#practiceInput2 {
    position: absolute;
    top: 175px;
    left: 23px;
}

#practiceInput3 {
    position: absolute;
    top: 230px;
    left: 23px;
}

#practiceInput4 {
    position: absolute;
    top: 285px;
    left: 23px;
}

#practiceInput5 {
    position: absolute;
    top: 340px;
    left: 23px;
}

#practiceInput6 {
    position: absolute;
    top: 395px;
    left: 23px;
}

.closer {
    position: absolute;
    left: 330px;
    top: 4px;
    width: 40px;
    height: 40px;
    text-align: center;
    font-size: 1.8em;
    padding: 2px;
    border: 2px solid black;
    border-radius: 3px;
    background-color: salmon;
    color: white;
}

.closer:hover {
    background-color: lightsalmon;
    color: black;
    cursor: pointer;
}

#wordPlayTitle {
  grid-column: 1 / 2;
  grid-row: 2;
  font-size: 1.2rem;
  transform: translateY(15px) translateX(10px);
  border-right: 4px solid black;
  padding-right: 2px;
  text-align: center;
}

#wordInfoDisplay {
  color: black;
  background-color: lavender;
  border: 8px solid salmon;
  border-radius: 10px;
  height: 208px;
  width: 390px;
  position: absolute;
  top: 119px;
  left: 320px;
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: repeat(8, 1fr);
  visibility: hidden;
}

#wordChosenTitle {
  grid-column: 1 / 2;
  grid-row: 1;
  font-size: 1.2rem;
  transform: translateY(5px) translateX(10px);
  border-right: 4px solid black;
  padding-right: 2px;
  text-align: center;
}

#wordChosen {
  grid-column: 3 / 6;
  grid-row: 1;
  font-size: 2rem;
  transform: translateX(-26px) translateY(5px);
}

#wordPracticeTitle {
  grid-column: 1 / 2;
  grid-row: 3;
  font-size: 1.2rem;
  transform: translateY(26px) translateX(10px);
  border-right: 4px solid black;
  padding-right: 4px;
  text-align: center;
}


#studentInput {
  position: absolute;
  font-size: 1.2rem;
  top: 145px;
  left: 108px;
  height: 2em;
  width: 200px;
  border-right: 4px solid black;
  border-radius: 3px;
  padding-right: 2px;
  background-color: lightcyan;
  text-align: left;
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

.imageAndWordContainer > span {
  padding-left: 5%;
  font-size: 0.7em;
  text-align: center;
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

#replaceableDomainText {
  position: absolute;
  top: 412px;
  left: 20px;
  font-size: 1.3rem;
  color: white;
  background-color: rgb(2, 124, 53);
  border-radius: 10px;
  padding-left: 3px;
  padding-right: 3px;
  border: 3px solid black;
  width: 215px;
  height: 34px;
  text-align: center;
  visibility: hidden;
  margin: auto;
}

#replaceableDomainText:hover {
  cursor: pointer;
  animation: buttonStuff 375ms forwards;
  color: black;
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

#soundPlayImage2 {
  position: absolute;
  top: 68px;
  left: 108px;
}

#soundPlayImage {
  position: absolute;
  top: 83px;
  left: 385px;
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

#replaceableText {
  margin: auto;
  width: 450px;
  min-height: 400px;
  margin-top: 10px;
  padding: 5px;
  background-color: lavender;
  color: black;
  font-size: 1.5em;
  border: 10px solid salmon;
  border-radius: 5px;
}

#dataAndImageContainer {
  display: flex;
  align-content: center;
}

#bigImage {
  max-height: 400px;
  max-width: 650px;
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

</style>