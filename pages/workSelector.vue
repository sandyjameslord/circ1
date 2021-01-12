<template>

    <div id='mainDiv'>
    
        <div id='titleBanner'>
            <img id="logo" style="cursor:pointer;" @click="goToCurriculum()" src="circleLOGO.png" alt="">
            <span id="worksheetOptionsText">Extensions for:</span>
            <p id="themeName">{{ this.theme }}   {{ this.unit }}</p>
        </div>
        <img id="expandingLogo" src="circleLOGO.png">
        <div id='allChoicesContainer'>
            <div @click="openWorksheet(1)" id="a1"><span id='a1TEXT'>E1</span><span id="activity1" class="activitySpan">Explore</span></div>
            <div @click="openWorksheet(2)" id="a2"><span id='a2TEXT'>E2</span><span id="activity2" class="activitySpan">Practice: Words</span></div>
            <div @click="openWorksheet(3)" id="a3"><span id='a3TEXT'>E3</span><span id="activity3" class="activitySpan">Practice: Sentences</span></div>
            <div @click="openWorksheet(4)" id="a4"><span id='a4TEXT'>E4</span><span id="activity4" class="activitySpan">Create: Sentences</span></div>
            <div @click="openWorksheet(5)" id="a5" ><span id='a5TEXT'>E5</span><span id="activity5" class="activitySpan">Speak: Words</span></div>
            <div @click="openWorksheet(6)"  id="a6"><span id='a6TEXT'>E6</span><span id="activity6" class="activitySpan">Speak: Sentences</span></div>
            <div @click="openWorksheet(7)"  id="a7"><span id='a7TEXT'>E7</span><span id="activity7" class="activitySpan">Discuss: Questions</span></div>
            <div @click="openWorksheet(8)"  id="a8"><span id='a8TEXT'>E8</span><span id="activity8" class="activitySpan">Discuss: Your Ideas</span></div>
        </div>

        <span id="a6Sent1" @click="openWorksheet('6A')" ></span>
        <span id="a6Sent2" @click="openWorksheet('6B')" ></span>
        <span id="a7Sent1" @click="openWorksheet('7A')" ></span>
        <span id="a7Sent2" @click="openWorksheet('7B')" ></span>
        <div id="horizontalLine"></div>

        <div id='imagesContainer'>
            <div v-for="(product, index) in products" :key="product._id">
                <div v-if="product.theme == theme">
                    <div v-if="product.unit == unit">
                        <div class="imageAndWordContainer">
                            <img class='smallImage' :id=index :src="product.photo" alt="">
                            
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
      unit: unit,
      theme: theme,
      title: titleee,
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
        return typeof title === 'function' ? title.call(vm) : title
    }
  },

    
    openWorksheet(number) {
      if (number == 1) {
        window.open ('worksheet01?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == 2) {
        window.open ('worksheet02?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == 3) {
        window.open ('worksheet03?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == 4) {
        window.open ('worksheet04?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == 5) {
        window.open ('worksheet5A?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == '6A') {
        window.open ('worksheet06A?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == '6B') {
        window.open ('worksheet06B?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == '7A') {
        window.open ('worksheet07A?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == '7B') {
        window.open ('worksheet07B?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
      if (number == 8) {
        window.open ('worksheet08?theme=' + this.theme + '&unit=' + this.unit, '_self',false)
      }
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

#a6Sent1 {
  position: absolute;
  top: 250px;
  left: 808px;
  background-color: lavender;
  border: 3px solid  rgb(32, 178, 170);;
  height: 25px;
  width: 55px;
  border-radius: 10px;
  opacity: 0;
  animation: fadeIn6 2000ms forwards; 
}

#a6Sent1:hover {
  background-color: green;
  border-color: salmon;
  color: white;
  cursor: pointer;
}

#a6Sent1::before {
  content: "Sent 1";
  position: absolute;
  top: 0px;
  left: 2px;
  width: 50px;
}

#a6Sent2 {
  position: absolute;
  top: 250px;
  left: 867px;
  background-color: lavender;
  border: 3px solid  rgb(32, 178, 170);;
  height: 25px;
  width: 55px;
  border-radius: 10px;
  animation: fadeIn6 2000ms forwards; 
}

#a6Sent2:hover {
  background-color: green;
  border-color: salmon;
  color: white;
  cursor: pointer;
}

#a6Sent2::before {
  content: "Sent 2";
  position: absolute;
  top: 0px;
  left: 2px;
  width: 50px;
}

#a7Sent1 {
  position: absolute;
  top: 410px;
  left: 907px;
  background-color: lavender;
  border: 3px solid  rgb(244, 164, 95);
  height: 25px;
  width: 55px;
  border-radius: 10px;
  animation: fadeIn7 2000ms forwards; 
}

#a7Sent1:hover {
  background-color: green;
  border-color: salmon;
  color: white;
  cursor: pointer;
}


#a7Sent1::before {
  content: "Sent 1";
  position: absolute;
  top: 0px;
  left: 2px;
  width: 50px;
}

#a7Sent2 {
  position: absolute;
  top: 410px;
  left: 967px;
  background-color: lavender;
  border: 3px solid  rgb(244, 164, 95);
  height: 25px;
  width: 55px;
  border-radius: 10px;
  animation: fadeIn7 2000ms forwards; 
}

#a7Sent2:hover {
  background-color: green;
  border-color: salmon;
  color: white;
  cursor: pointer;
}

#a7Sent2::before {
  content: "Sent 2";
  position: absolute;
  top: 0px;
  left: 2px;
  width: 50px;
}

#a1TEXT {
  position: absolute;
  font-size: 1.3em;
  top: 22px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity1 {
  position: absolute;
  top: 70px;
  left: 35px;
  text-align: center;
}

#a2TEXT {
  position: absolute;
  font-size: 1.3em;
  top: 22px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity2 {
  position: absolute;
  top: 70px;
  left: 5px;
  text-align: center;
}

#a3TEXT {
  position: absolute;
  font-size: 1.3em;
  top: 15px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity3 {
  position: absolute;
  top: 63px;
  left: 5px;
  text-align: center;
}

#a4TEXT {
  position: absolute;
  font-size: 1.3em;
  top: 15px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity4 {
  position: absolute;
  top: 63px;
  left: 5px;
  text-align: center;
}

#a5TEXT {
  position: absolute;
  font-size: 1.3em;
  top: 15px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity5 {
  position: absolute;
  top: 63px;
  left: 5px;
  text-align: center;
}

#a6TEXT {
  position: absolute;
  font-size: 1.3em;
  top: -4px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity6 {
  position: absolute;
  top: 40px;
  left: 5px;
  text-align: center;
}

#a7TEXT {
  position: absolute;
  font-size: 1.3em;
  top: -4px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity7 {
  position: absolute;
  top: 40px;
  left: 5px;
  text-align: center;
}

#a8TEXT {
  position: absolute;
  font-size: 1.3em;
  top: 15px;
  left: 37px;
  text-align: center;
  width: 80px;
  border-bottom: 4px solid salmon;
}

#activity8 {
  position: absolute;
  top: 63px;
  left: 5px;
  text-align: center;
}

#expandingLogo {
  position: absolute;
  top: 330px;
  left: 450px;
}

.smallImageTitle {
  font-size: 0.7em;
}

#mainDiv {
    display: grid;
    grid-template-columns: repeat(10, 1fr);
    grid-template-rows: 1fr 7fr 1fr 2fr;
}

#titleBanner {
    grid-column: 1 / 11;
    grid-row: 1;
    display: grid;
    grid-template-columns: 90px 1fr 1fr 1fr;
    height: 80px;
    align-items: center; 
    visibility: visible;
    background-color: salmon;
    border-bottom: 2px solid rgb(1, 58, 1);
}

#allChoicesContainer {
    grid-column: 1 / 11;
    grid-row: 2;
}

#allChoicesContainer > div {
    position: absolute;
    min-height: 170px;
    min-width: 170px;
    max-height: 170px;
    max-width: 170px;
    border-radius: 50%;
    background-color: lavender;
    color: black;
    font-size: 1.6em;
    text-align: center;
}

.activitySpan {
  position: relative;
  top: 31px;
}

#a1 {
  opacity: 0;
  top: 465px;
  left: 220px;
  border: 8px solid rgb(250, 250, 210);
  animation: fadeIn1 2000ms forwards;
}

#a2 {
  opacity: 0;
  top: 295px;
  left: 150px;
  border: 8px solid rgb(144, 238, 144);
  animation: fadeIn2 2000ms forwards;
}

#a3 {
  opacity: 0;
  top: 135px;
  left: 242px;
  border: 8px solid  rgb(211, 211, 211);
  animation: fadeIn3 2000ms forwards;
}

#a4 {
  opacity: 0;
  top: 90px;
  left: 420px;
  border:  8px solid rgb(240, 128, 128);
  animation: fadeIn4 2000ms forwards;
}

#a5 {
  opacity: 0;
  top: 90px;
  left: 604px;
  border:  8px solid rgb(253, 182, 193);
  animation: fadeIn5 2000ms forwards;
}

#a6 {
  opacity: 0;
  top: 135px;
  left: 780px;
  border:  8px solid rgb(32, 178, 170);
  animation: fadeIn6 2000ms forwards;
}

#a7 {
  opacity: 0;
  top: 295px;
  left: 880px;
  border:  8px solid rgb(244, 164, 95);
  animation: fadeIn7 2000ms forwards;
}

#a8 {
    opacity: 0;
  top: 465px;
  left: 809px;
    border:  8px solid rgb(46, 139, 87);
    animation: fadeIn8 2000ms forwards;
}

#a1:hover, #a2:hover, #a3:hover, #a4:hover, #a5:hover, #a8:hover {
    cursor: pointer;
    background-color: green;
    color: white;
}

@keyframes fadeIn1 {
    0% {opacity: 0;}
    10% {opacity: 0;}
    20% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes fadeIn2 {
    0% {opacity: 0;}
    20% {opacity: 0;}
    30% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes fadeIn3 {
    0% {opacity: 0;}
    30% {opacity: 0;}
    40% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes fadeIn4 {
    0% {opacity: 0;}
    40% {opacity: 0;}
    50% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes fadeIn5 {
    0% {opacity: 0;}
    50% {opacity: 0;}
    60% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes fadeIn6 {
    0% {opacity: 0;}
    60% {opacity: 0;}
    70% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes fadeIn7 {
    0% {opacity: 0;}
    70% {opacity: 0;}
    80% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes fadeIn8 {
    0% {opacity: 0;}
    80% {opacity: 0;}
    90% {  opacity: 1;}
    100% {  opacity: 1;}
}

@keyframes getBigger {
  0% {border-radius: 50%;}
  50% {border-radius: 40%;}
  100% {border-radius: 40%;}
}

#horizontalLine {
    grid-row: 3;
    grid-column: 1 / 11;
    height: 30px;
    background-color: salmon;
    border-top: 4px solid darkgreen;
    margin-bottom: 5px;
}

#imagesContainer {
    grid-row: 4;
    display: flex;
    margin: auto;
}

#logo {
  height: 65px;
  transform: translateX(15px) translateY(-1px);
  border-radius: 10px;
}

#worksheetOptionsText {
    grid-column: 2;
    font-size: 2.5em;
    text-align: right;
    min-width: 377px;
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
    transform: scale(0.9) translateX(200px);
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

</style>