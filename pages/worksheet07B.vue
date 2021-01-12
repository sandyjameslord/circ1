<template>

  <div id='mainDiv'>
    
    
    <div id='nonViewDataContainer'>
      <p id="vocabInfo">Click an image below to begin.</p>
      <p id="bcSentenceInfo"></p>

    </div>
    
    <div id='titleBanner'>
      <img id="logo" style="cursor:pointer;" @click="goToCurriculum()" src="circleLOGO.png" alt="">
      <span id="nameOfWorksheet">Extension 7: Discuss Questions 2</span>
      <p id="themeName" @click="backToSelector()">{{ this.theme }}   {{ this.unit }}</p>
    </div>

    <div id="recording"></div>
    <div id='recordingText'></div>
    <div id="period1">.</div>
    <div id="period2">.</div>
    <div id="period3">.</div>
    <div id="questionType"></div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(1); onStartClickAnimation(1)" class="buttonStart" id="buttonStart1"></span><br />
      <span @click="onStopClickAnimation(1)" id="buttonStop1" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(2); onStartClickAnimation(2)"  class="buttonStart" id="buttonStart2"></span><br />
      <span  @click="onStopClickAnimation(2)" id="buttonStop2" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(3); onStartClickAnimation(3)"  class="buttonStart" id="buttonStart3"></span><br />
      <span  @click="onStopClickAnimation(3)" id="buttonStop3" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(4); onStartClickAnimation(4)"  class="buttonStart" id="buttonStart4"></span><br />
      <span  @click="onStopClickAnimation(4)" id="buttonStop4" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(5); onStartClickAnimation(5)"  class="buttonStart" id="buttonStart5"></span><br />
      <span  @click="onStopClickAnimation(5)" id="buttonStop5" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(6); onStartClickAnimation(6)"  class="buttonStart" id="buttonStart6"></span><br />
      <span  @click="onStopClickAnimation(6)" id="buttonStop6" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(7); onStartClickAnimation(7)"  class="buttonStart" id="buttonStart7"></span><br />
      <span  @click="onStopClickAnimation(7)" id="buttonStop7" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(8); onStartClickAnimation(8)"  class="buttonStart" id="buttonStart8"></span><br />
      <span  @click="onStopClickAnimation(8)" id="buttonStop8" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(9); onStartClickAnimation(9)"  class="buttonStart" id="buttonStart9"></span><br />
      <span  @click="onStopClickAnimation(9)" id="buttonStop9" class="buttonStop" ></span>
    </div>

    <div class='buttonsContainer'>
      <span @click="turnMicOnOff(10); onStartClickAnimation(10)"  class="buttonStart" id="buttonStart10"></span><br />
      <span  @click="onStopClickAnimation(10)" id="buttonStop10" class="buttonStop" ></span>
    </div>

    <div id="audioStuff">
        <audio class="audioClass" id="aud1" controls></audio>
        <audio class="audioClass" id="aud2" controls></audio>
        <audio class="audioClass" id="aud3" controls></audio>
        <audio class="audioClass" id="aud4" controls></audio>
        <audio class="audioClass" id="aud5" controls></audio>
        <audio class="audioClass" id="aud6" controls></audio>
        <audio class="audioClass" id="aud7" controls></audio>
        <audio class="audioClass" id="aud8" controls></audio>
        <audio class="audioClass" id="aud9" controls></audio>
        <audio class="audioClass" id="aud10" controls></audio>
        
        <audio class="audioControlClass" id="audioControl1" ></audio>
        <audio class="audioControlClass" id="audioControl2" ></audio>
        <audio class="audioControlClass" id="audioControl3" ></audio>
        <audio class="audioControlClass" id="audioControl4" ></audio>
        <audio class="audioControlClass" id="audioControl5" ></audio>
        <audio class="audioControlClass" id="audioControl6" ></audio>
        <audio class="audioControlClass" id="audioControl7" ></audio>
        <audio class="audioControlClass" id="audioControl8" ></audio>
        <audio class="audioControlClass" id="audioControl9" ></audio>
        <audio class="audioControlClass" id="audioControl10" ></audio>
    </div>

    <div id='playPauseVolumeButtons'> 
        <span class="playButton" id='playButton1' @click="onPlayClickAnimation(1)"></span> 
        <span class="playButton" id='playButton2' @click="onPlayClickAnimation(2)"></span> 
        <span class="playButton" id='playButton3' @click="onPlayClickAnimation(3)"></span> 
        <span class="playButton" id='playButton4' @click="onPlayClickAnimation(4)"></span> 
        <span class="playButton" id='playButton5' @click="onPlayClickAnimation(5)"></span> 
        <span class="playButton" id='playButton6' @click="onPlayClickAnimation(6)"></span> 
        <span class="playButton" id='playButton7' @click="onPlayClickAnimation(7)"></span> 
        <span class="playButton" id='playButton8' @click="onPlayClickAnimation(8)"></span> 
        <span class="playButton" id='playButton9' @click="onPlayClickAnimation(9)"></span> 
        <span class="playButton" id='playButton10' @click="onPlayClickAnimation(10)"></span> 
    </div>

    <div id="dataAndImageContainer">   
        <div id='actualImageContainer'>
        <img id="bigImage" src="circleLOGO.png" alt="">
    </div>  
    <div id="studentInputContainer">

        <p class='sentenceInfo' id="abSentenceInfo">Click an image below. Then click 'Start' and practice repeating the words. Click 'Stop', then listen to yourself.</p>
        <div class='soundPlayImage' id="soundPlayImage1" @click="playSound()"> > </div>
    </div>
      
    </div>
    
    <div id="horizontalLine"></div>

    <div class='imagesContainer'>
      <div v-for="(product, index) in products" :key="product._id">
        <div v-if="product.theme == theme">
          <div v-if="product.unit == unit">
            <div class="imageAndWordContainer">
              <img class='smallImage' :id=index @click="makeImageBig(index, product.bcQuestion, product.bcQuestionDomain)" :src="product.photo" alt="">

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
      onStartClickAnimation(index) {
            let playButton = document.getElementById("playButton" + index);
            playButton.style.animationDuration = "0ms";

            let startButton = document.getElementById("buttonStart" + index);
            startButton.style.animationDuration = "0ms";
            
            let stopButton = document.getElementById("buttonStop" + index);
            stopButton.style.animationDuration = "3000ms";
            
            let recording = document.getElementById("recording");
            recording.style.animationDuration = "3000ms";

            let recordingText = document.getElementById("recordingText");
            let period1 = document.getElementById("period1");
            let period2 = document.getElementById("period2");
            let period3 = document.getElementById("period3");

            recordingText.style.visibility = "visible";
            period1.style.visibility = "visible";
            period2.style.visibility = "visible";
            period3.style.visibility = "visible";

            recordingText.style.animationDuration = "3000ms";
            recordingText.style.border = "0px";
            recordingText.style.backgroundColor = "inherit";

            period1.style.animationDuration = "3000ms";
            period2.style.animationDuration = "3000ms";
            period3.style.animationDuration = "3000ms";

      },
      onStopClickAnimation(index) {
          let recording = document.getElementById("recording");
          recording.style.animationDuration = "0ms";
          recording.style.backgroundColor = "yellow";
          let stopButton = document.getElementById("buttonStop" + index);
          stopButton.style.animationDuration = "0ms";
      
          let recordingText = document.getElementById("recordingText");
          let period1 = document.getElementById("period1");
          let period2 = document.getElementById("period2");
          let period3 = document.getElementById("period3");
            
          recordingText.style.paddingLeft = "38px";
          recordingText.style.paddingRight = "38px";
          recordingText.style.paddingTop = "4px";
          recordingText.style.paddingBottom = "4px";
          recordingText.style.border = "4px solid darkgreen";
          recordingText.style.backgroundColor = "lightgreen";
          recordingText.style.borderRadius = "55px";
          recordingText.style.transform = "translateX(13px) translateY(-7px)";
          recordingText.style.visibility = "hidden";
          period1.style.visibility = "hidden";
          period2.style.visibility = "hidden";
          period3.style.visibility = "hidden";
            
          recordingText.style.animationDuration = "0ms";
          period1.style.animationDuration = "0ms";
          period2.style.animationDuration = "0ms";
          period3.style.animationDuration = "0ms";

          let playButton = document.getElementById("playButton" + index);
          playButton.style.animationDuration = "3000ms";
          playButton.style.animationDelay = "1000ms";

          let startButton = document.getElementById("buttonStart" + index);
          startButton.style.animationDuration = "3000ms";
      },
      onPlayClickAnimation(index) {
          let control = document.getElementById('audioControl' + index); 
          control.play();
      },
        
      turnMicOnOff(index) {
          let constraintObj = {
                audio: {
                    echoCancellation: true,
                    output: false,
                }
            };
            if (navigator.mediaDevices === undefined) {
                navigator.mediaDevices = {};

                navigator.mediaDevices.getUserMedia = function (constraintObj) {
                    let getUserMedia =
                    navigator.webkitGetUserMedia || navigator.mozGetUserMedia;
                    if (!getUserMedia) {
                        return Promise.reject(
                            new Error("getUserMedia is not implemented in this browser")
                        );
                    }
                    return new Promise(function (resolve, reject) {
                        getUserMedia.call(navigator, constraintObj, resolve, reject);
                    }
                    );
                };
            } else {
                navigator.mediaDevices
                    .enumerateDevices()
                    .then((devices) => {
                        devices.forEach((device) => {
                            console.log(device.kind.toUpperCase(), device.label);
                            //, device.deviceId
                        });
                    })
                    .catch((err) => {
                        console.log(err.name, err.message);
                    });
            }
                navigator.mediaDevices
                    .getUserMedia(constraintObj)
                    .then(function (mediaStreamObj) {
                      let audioString = "aud" + index;
                      let audio = document.getElementById(audioString);
                      if ("srcObject" in audio) {
                        audio.srcObject = mediaStreamObj;
                      } else {
                        audio.src = window.URL.createObjectURL(mediaStreamObj);
                      }
          let startText = "buttonStart" + index;
          let stopText = "buttonStop" + index;

          let start = document.getElementById(startText);
          let stop = document.getElementById(stopText);
    

          let bigImg = document.getElementById("bigImage");
          let imageAudioSaveNumber1 = "audioControl" + index;

          let audSave = document.getElementById(imageAudioSaveNumber1);
          let mediaRecorder = new MediaRecorder(mediaStreamObj);
          let chunks = [];
          mediaRecorder.start();

          stop.addEventListener("click", (ev) => {
            mediaRecorder.stop();
            console.log(mediaRecorder.state);
          });
          mediaRecorder.ondataavailable = function (ev) {
            chunks.push(ev.data);
          };
          mediaRecorder.onstop = (ev) => {
            let blob = new Blob(chunks, { type: "audio/mp3;" });
            chunks = [];
            let audioURL = window.URL.createObjectURL(blob);
            audSave.src = audioURL;
          };
        })
        .catch(function (err) {
          console.log(err.name, err.message);
        });
      },
      onResult (data) {
          console.log('The blob data:', data);
          console.log('Downloadable audio', window.URL.createObjectURL(data));
      },
      getTitle (vm) {
          const { title } = vm.$options
          if (title) {
              return typeof title === 'function'
                  ? title.call(vm)
                  : title
          }
      },
      playSound(){
          let studentInput = document.getElementById("abSentenceInfo");
          let speech = new SpeechSynthesisUtterance();      
          speech.text = studentInput.innerText;
          
          window.speechSynthesis.speak(speech);
      },
      makeImageBig(index, vocab, questionType) {
          let quesTyp = document.getElementById('questionType');
          quesTyp.style.visibility = "visible";
          this.turnMicOnOff(index);

          let startButtons = [
            "buttonStart1", 
            "buttonStart2", 
            "buttonStart3", 
            "buttonStart4", 
            "buttonStart5", 
            "buttonStart6", 
            "buttonStart7", 
            "buttonStart8", 
            "buttonStart9", 
            "buttonStart10",
          ]

          let stopButtons = [
            "buttonStop1", 
            "buttonStop2", 
            "buttonStop3", 
            "buttonStop4", 
            "buttonStop5", 
            "buttonStop6", 
            "buttonStop7", 
            "buttonStop8", 
            "buttonStop9", 
            "buttonStop10",
          ]

          let audioControls = [
            "audioControl1",
            "audioControl2",
            "audioControl3",
            "audioControl4",
            "audioControl5",
            "audioControl6",
            "audioControl7",
            "audioControl8",
            "audioControl9",
            "audioControl10",
          ]

          let playButtons = [
            "playButton1",
            "playButton2",
            "playButton3",
            "playButton4",
            "playButton5",
            "playButton6",
            "playButton7",
            "playButton8",
            "playButton9",
            "playButton10",
          ]

          let recordingA = document.getElementById("recording");
          let recordingTextA = document.getElementById("recordingText");
          let period1A =  document.getElementById("period1");
          let period2A =  document.getElementById("period2");
          let period3A =  document.getElementById("period3");

          let fullText;
          if (questionType == 'SS') {fullText = 'Social Studies'}
          if (questionType == 'SC') {fullText = 'Science'}
          if (questionType == 'MA') {fullText = 'Mathematics'}
          if (questionType == 'LA') {fullText = 'Language Arts'}
          if (questionType == 'EDL') {fullText = 'Every Day Language'}

          quesTyp.innerText = fullText;

          recordingA.style.visibility = "visible";


          for (let i = 0; i < 10; i++) {
              if ((index % 10) == i) {
                  document.getElementById(startButtons[i]).style.visibility = "visible";
                  document.getElementById(stopButtons[i]).style.visibility = "visible";
                  document.getElementById(audioControls[i]).style.visibility = "visible";
                  document.getElementById(playButtons[i]).style.visibility = "visible";
              }
          }

          for (let i = 0; i < 10; i++) {
              let strtbtn1 = document.getElementById(startButtons[i]);
              let stpbtn1 =  document.getElementById(stopButtons[i]);        
              let audctrl1 =  document.getElementById(audioControls[i]);
              let plbtn = document.getElementById(playButtons[i]);

              strtbtn1.style.visibility = "hidden";
              stpbtn1.style.visibility = "hidden";
              audctrl1.style.visibility = "hidden";
              plbtn.style.visibility = "hidden";
          }
      
          for (let i = 0; i < 10; i++) {
              if ((index % 10) == i) {
                  document.getElementById(startButtons[i]).style.visibility = "visible";
                  document.getElementById(stopButtons[i]).style.visibility = "visible";
                  document.getElementById(audioControls[i]).style.visibility = "visible";
                  document.getElementById(playButtons[i]).style.visibility = "visible";
              }
          }
          let textInfo = document.getElementById('abSentenceInfo');
          textInfo.innerText = vocab;
          textInfo.style.fontSize = "1.3em";
          textInfo.style.textAlign = "left";

          let bigImage = document.getElementById("bigImage");
          let littleImageSource = document.getElementById(index).src;
          
          bigImage.src = littleImageSource;
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

#questionType {
    position: absolute;
    top: 410px;
    left: 30px;
    height: 80px;
    width: 245px;
    background-color: lavender;
    border: 8px solid salmon;
    border-radius: 25px;
    font-size: 1.6em;
    visibility: hidden;
    text-align: center;
    padding-top: 13px;
}

#period1 {
    position: absolute;
    top: -47px;
    left: 65px;
    font-size: 18em;
    animation: period1Blink  infinite;
    visibility: hidden;
}

#period2 {
    position: absolute;
    top: -47px;
    left: 125px;
    font-size: 18em;
    animation: period2Blink  infinite;
    visibility: hidden;
}

#period3 {
    position: absolute;
    top: -47px;
    left: 185px;
    font-size: 18em;
    animation: period3Blink  infinite;
    visibility: hidden;
}

@keyframes period1Blink {
    0% {opacity: 0}
    15% {opacity: 0}
    25% {opacity: 1}
    97% {opacity: 1}
    100% {opacity: 0}
}

@keyframes period2Blink {
    0% {opacity: 0}
    40% {opacity: 0}
    50% {opacity: 1}
    97% {opacity: 1}
    100% {opacity: 0}
}

@keyframes period3Blink {
    0% {opacity: 0}
    65% {opacity: 0}
    75% {opacity: 1}
    97% {opacity: 1}
    100% {opacity: 0}
}

#recordingText {
    position: absolute;
    top: 350px;
    left: 46px;
    font-size: 2.5em;
    visibility: hidden;
}

@keyframes startButtonAnimation {
    0% {
        opacity: 0.8;
        background-color: green;
        color: white;
    }
    50% {
        opacity: 1;
        background-color: lightgreen;
        color: black;
    }
    100% {
        opacity: 0.8;
        background-color: green;
        color: white;
    }
}

@keyframes stopButtonAnimation {
    0% {
        opacity: 0.8;
        background-color: red;
        color: white;
    }
    50% {
        opacity: 1;
        background-color: pink;
        color: black;
    }
    100% {
        opacity: 0.8;
        background-color: red;
        color: white;
    }
}

@keyframes recordingAnimation {
        0% {
        opacity: 0.8;
        background-color: green;
        color: white;
        border-width: 4px;
    }
    50% {
        opacity: 1;
        background-color: yellow;
        color: black;
        border-width: 20px;
    }
    100% {
        opacity: 0.8;
        background-color: green;
        color: white;
        border-width: 4px;
    }
}

@keyframes playButtonAnimation {    0% {
        opacity: 0.8;
        background-color: green;
        color: white;
    }
    50% {
        opacity: 1;
        background-color: lavender;
        color: black;
    }
    100% {
        opacity: 0.8;
        background-color: green;
        color: white;
    }
}

#recording {
    position: absolute;
    
    top: 170px;
    left: 20px;
    width: 270px;
    height: 100px;
    background-color: green;
    border: 8px solid salmon;
    border-radius: 55px;
    animation: recordingAnimation infinite;
    visibility: hidden;

}

#playPauseVolumeButtons {
    position: absolute;
    top: 270px;
    left: 52px;
}

.playButton {
    position: absolute;
    top: 0px;
    left: -18px;
    height: 120px;
    width: 220px;
    white-space: pre;
    background-color: green;
    padding: 10px;
    color:white;
    margin: 10px;
    font-size: 2em;
    border: 8px solid salmon;
    border-radius: 25px;
    visibility: hidden;
    animation: playButtonAnimation infinite;
}

.playButton::after {
    content: "Play";
    position: absolute;
    top: -5px;
    left: 16px;
    font-size: 2.8em;
}

.soundPlayImage {
    position: absolute;
    top: 25px;
    left: 1000px;
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

@keyframes buttonStuff {
  0% {background-color: rgb(2, 124, 53);}
  100% {background-color: lightsalmon;}
}

@keyframes afterStuff {
  0% {opacity: 0;background-color: rgb(2, 124, 53);}
  100% {opacity: 1;background-color:lightsalmon;}
}

@keyframes startBlinker {
  0% {
    opacity: 0.8;
    background-color: green;
    color: white;
  }
  50% {
    opacity: 1;
    background-color: lightgreen;
    color: black;
  }
  100% {opacity: 0.8;
    background-color: green;
    color: white;}
}

@keyframes stopBlinker {
  0% {
    opacity: 0.8;
    background-color: red;
    color: white;
  }
  50% {
    opacity: 1;
    background-color: pink;
    color: black;
  }
  100% {opacity: 0.8;
    background-color: red;
    color: white;}
}

.buttonStart::after {
  content: "Start";
  position: absolute;
  top: 20px;
  left: 7px;
}

.buttonStop::after {
  content: "Stop";
  position: absolute;
  top: 20px;
  left: 9px;
}

.buttonStart {
  position: absolute;
  top: 60px;
  left: 40px;
  width: 100px;
  height: 100px;
  background-color: green;
  border-radius: 50%;
  font-size: 2em;
  border: 8px solid salmon;
  animation: startBlinker 3000ms infinite;
  cursor: pointer;
  z-index: 999999999;
  visibility: hidden;
}

.buttonStop {
  position: absolute;
  cursor: pointer;
  top: 60px;
  left: 175px;
  width: 100px;
  height: 100px;
  background-color: red;
  border-radius: 50%;
  font-size: 2em;
  border: 8px solid salmon;
  animation: stopBlinker infinite;
  animation-delay: 1500ms;
  z-index: 999999999;
  visibility: hidden;
}

#audioStuff {
  position: absolute;
}

.buttonsContainer {
  position: absolute;
  top: 0px;
}

.audioClass {
  visibility: hidden;
}

.audioControlClass {
  position: absolute;
  top: 150px;
  left: 10px;
  border: 8px solid salmon;
  border-radius: 27px;
  z-index: 4242424242424242;
  filter: sepia(20%) saturate(70%) grayscale(1) contrast(99%) invert(12%);
  font-size: 3em;
    width: 250px;
    height: 40px;
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
  transform: translateY(-20px);
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
    width: 1000px;
    height: 120px;
    background-color: lavender;
    border: 8px solid salmon;
    border-radius: 25px;
    transform: translateX(-50px);
}

.practiceInput {
    height: 2.5em;
    width: 713px;
    font-size: 1.4em;
    margin: 10px;
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
  transform: translateX(150px);
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