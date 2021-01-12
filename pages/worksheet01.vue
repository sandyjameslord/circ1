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
      <span id="nameOfWorksheet">Extension 1: Explore</span>
      <p id="themeName" @click="backToSelector()">{{ this.theme }}   {{ this.unit }}</p>
    </div>

    <div id="tellAboutWordClick">Click on a word above to learn more.</div>
    <div id="tellAboutWordClickAbove1"></div>
    <div id="tellAboutWordClickAbove2"></div>



    <div id="dataAndImageContainer">  
      <div id='textContainer'>
        <div id="textAndDomainContainer">
            <p class='replaceableText clickable' @click="getWord()" id='replaceableText' style="font-size: 2rem;">Click on an image below to begin.</p>
        </div>
        <div id='buttonsContainer'>
          <p id='vocab' @click="addVocab()">Word</p>
          <p id='abSentence' @click="addABSentence()">Sent 1</p>
          <p id='bcSentence' @click="addBCSentence()">Sent 2</p>
          <p id='abQuestion' @click="addABQuestion()">Q 1</p>
          <p id='bcQuestion' @click="addBCQuestion()">Q 2</p>
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
      <p id="wordPracticeTitle">Practice writing</p>
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
        backToSelector(){
            window.open ('workSelector?theme=' + this.theme + '&unit=' + this.unit,'_self',false)
        },
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
        let word = document.getElementById("wordChosen");
        
        let studInp = document.getElementById("studentInput");
        if (studInp.value == word.textContent) {
          studInp.style.backgroundColor = "lightgreen";
        } else {
          studInp.style.backgroundColor = "white";
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
            let replaceableText = document.getElementById("replaceableText");
            replaceableText.style.opacity = "1";
            
            let tellAboutWord = document.getElementById("tellAboutWordClick");
            let tellAboutWord1 = document.getElementById("tellAboutWordClickAbove1");
            let tellAboutWord2 = document.getElementById("tellAboutWordClickAbove2");
            
            tellAboutWord.style.visibility = "hidden";
            tellAboutWord1.style.visibility = "hidden";
            tellAboutWord2.style.visibility = "hidden";

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
        }
        );
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
      firstText.innerHTML = this.products[index].vocabulary;
      firstText.style.fontSize = "2.5rem";
      let vocab = document.getElementById("vocabInfo");
      vocab.innerHTML = this.products[index].vocabulary;

      let abSentence = document.getElementById("abSentenceInfo");
      abSentence.innerHTML = this.products[index].abSentence;

      let bcSentence = document.getElementById("bcSentenceInfo");
      bcSentence.innerHTML = this.products[index].bcSentence;

      let abQuestion = document.getElementById("abQuestionInfo");
      abQuestion.innerHTML = this.products[index].abQuestion;

      let bcQuestion = document.getElementById("bcQuestionInfo");
      bcQuestion.innerHTML = this.products[index].bcQuestion;

      let abQuestionDomain = document.getElementById("abQuestionDomain");
      abQuestionDomain.innerHTML = this.products[index].abQuestionDomain;

      let bcQuestionDomain = document.getElementById("bcQuestionDomain");
      bcQuestionDomain.innerHTML = this.products[index].bcQuestionDomain;

      let domainType = document.getElementById("replaceableDomainText");
      domainType.style.visibility = "hidden";

      let infoDisplay = document.getElementById("wordInfoDisplay");
      infoDisplay.style.visibility = "hidden";
    
    },
    addVocab() {
      let replaceableText = document.getElementById("replaceableText");
      let vocabInfo = document.getElementById("vocabInfo");
      replaceableText.innerHTML = vocabInfo.innerHTML;
      replaceableText.style.fontSize = "2.5rem";

      let domainType = document.getElementById("replaceableDomainText");
      domainType.style.visibility = "hidden";

      let infoDisplay = document.getElementById("wordInfoDisplay");
      infoDisplay.style.visibility = "hidden";
    },
    addABSentence() {
      let replaceableText = document.getElementById("replaceableText");
      let abSentenceInfo = document.getElementById("abSentenceInfo");
      replaceableText.innerHTML = abSentenceInfo.innerHTML;
      replaceableText.style.fontSize = "2rem";

      let domainType = document.getElementById("replaceableDomainText");
      domainType.style.visibility = "hidden";

      let infoDisplay = document.getElementById("wordInfoDisplay");
      infoDisplay.style.visibility = "hidden";
    },
    addBCSentence() {
      let replaceableText = document.getElementById("replaceableText");
      let bcSentenceInfo = document.getElementById("bcSentenceInfo");
      replaceableText.innerHTML = bcSentenceInfo.innerHTML;
      replaceableText.style.fontSize = "2rem";

      let domainType = document.getElementById("replaceableDomainText");
      domainType.style.visibility = "hidden";

      let infoDisplay = document.getElementById("wordInfoDisplay");
      infoDisplay.style.visibility = "hidden";
    },
    addABQuestion() {
      let replaceableText = document.getElementById("replaceableText");
      let abQuestionInfo = document.getElementById("abQuestionInfo");
      replaceableText.innerHTML = abQuestionInfo.innerHTML;
      replaceableText.style.fontSize = "1.4rem";

      let domainType = document.getElementById("replaceableDomainText");
      let abDomainType = document.getElementById("abQuestionDomain");
      
      let tempDomainType = abDomainType.innerHTML;
      if (tempDomainType == "SC") {tempDomainType = "Science"}
      else if (tempDomainType == "MA") {tempDomainType = "Mathematics"}
      else if (tempDomainType == "SS") {tempDomainType = "Social Studies"}
      else if (tempDomainType == "LA") {tempDomainType = "English Language Arts"}
      else if (tempDomainType == "EDL") {tempDomainType = "Every-Day Language"}
      domainType.innerHTML = tempDomainType;

      domainType.style.visibility = "visible";

      let infoDisplay = document.getElementById("wordInfoDisplay");
      infoDisplay.style.visibility = "hidden";
    },
    addBCQuestion() {
      let replaceableText = document.getElementById("replaceableText");
      let bcQuestionInfo = document.getElementById("bcQuestionInfo");
      replaceableText.innerHTML = bcQuestionInfo.innerHTML;
      replaceableText.style.fontSize = "1.2rem";

      let domainType = document.getElementById("replaceableDomainText");
      let bcDomainType = document.getElementById("bcQuestionDomain");
      
      let tempDomainType = bcDomainType.innerHTML;
      if (tempDomainType == "SC") {tempDomainType = "Science"}
      else if (tempDomainType == "MA") {tempDomainType = "Mathematics"}
      else if (tempDomainType == "SS") {tempDomainType = "Social Studies"}
      else if (tempDomainType == "LA") {tempDomainType = "English Language Arts"}
      else if (tempDomainType == "EDL") {tempDomainType = "Every-Day Language"}
      domainType.innerHTML = tempDomainType;

      domainType.style.visibility = "visible";

      let infoDisplay = document.getElementById("wordInfoDisplay");
      infoDisplay.style.visibility = "hidden";
    },
    goToCurriculum() {
      window.open ('curriculum4','_self',false)
    },
    getInfo(){
        return this.theme;
    }
  },

};

</script>

<style>

/* @import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap'); */

body {
  background-color: lightcyan;
  /* font-family: 'Lato', sans-serif; */
}

#tellAboutWordClickAbove1 {
  position: absolute;
  top: 252px;
  left: 113px;
  text-align: center;
  width: 82px;
  height: 40px;
  background-color: rgb(247, 197, 71);
  border: 4px solid rgb(66, 66, 101);
  border-radius: 10px;
  border-top-left-radius: 35%;
  border-top-right-radius: 35%;
  opacity: 1;
  z-index: 4242;
  animation: wordClickAnim1 4000ms infinite;
}

#tellAboutWordClickAbove2 {
  position: absolute;
  top: 222px;
  left: 144px;
  text-align: center;
  width: 20px;
  height: 20px;
  background-color: rgb(247, 197, 71);
  border: 4px solid rgb(66, 66, 101);
  border-radius: 25%;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
  opacity: 1;
  z-index: 4242;
  animation: wordClickAnim2 4000ms infinite;
}

#tellAboutWordClick {
  position: absolute;
  top: 305px;
  left: 53px;
  text-align: center;
  width: 202px;
  background-color: rgb(247, 197, 71);
  border: 4px solid rgb(66, 66, 101);
  border-radius: 10px;
  border-top-left-radius: 20%;
  border-top-right-radius: 20%;
  font-size: 1.5em;
  opacity: 1;
  z-index: 4242;
  animation: wordClickAnim 4000ms infinite;
}

@keyframes wordClickAnim {
  0% {transform: translateY(0px);}
  50% {transform: translateY(-30px);}
  98% {transform: translateY(0px);}
  100% {transform: translateY(0px);}
}

@keyframes wordClickAnim1 {
  0% {transform: translateY(0px);}
  55% {transform: translateY(-30px);}
  98% {transform: translateY(0px);}
  100% {transform: translateY(0px);}
}

@keyframes wordClickAnim2 {
  0% {transform: translateY(0px);}
  60% {transform: translateY(-30px);}
  98% {transform: translateY(0px);}
  100% {transform: translateY(0px);}
}

.imageAndWordContainer > span {
  padding-left: 5%;
  font-size: 0.7em;
  text-align: center;
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
  top: 401px;
  left: 238px;
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
  width: 300px;
  min-height: 400px;
  margin-top: 10px;
  padding: 5px;
  background-color: rgb(0, 87, 36);
  color: white;
  font-size: 1.2em;
  border: 10px solid salmon;
  border-radius: 5px;
  opacity: 0.2;
}

#dataAndImageContainer {
  display: flex;
  align-content: center;
}

#bigImage {
  max-width: 650px;
  max-height: 450px;
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

</style>