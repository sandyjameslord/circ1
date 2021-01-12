<template>
    <div>

        <div id="navbar">
            <span id='span1'><img @click="backToMain()" id='logoFinal' src="/circleLOGO.png" alt=""></span>
            <span id='curriculumHeader'>Themes and Units</span>
        </div>

        <div id="optionsBar">
            <div id="whatToDo">
                Hover on a theme, then select a unit.
            </div>
        </div>

        <div id="themeContainer">
            
            <div id="bodyTheme" @mouseover="addLine('body')"><img src="/imagesForThemes/body.svg" alt=""><span>Body</span></div>
            <div id="colorTheme" @mouseover="addLine('color')"><img src="/imagesForThemes/color.svg" alt=""><span>Color</span></div>
            <div id="fallTheme" @mouseover="addLine('fall')"><img src="/imagesForThemes/fall.svg" alt=""><span>Fall</span></div>        
            <div id="geographyTheme" @mouseover="addLine('geography')"><img src="/imagesForThemes/geography.svg" alt=""><span>Geography</span></div>
            <div id="houseTheme" @mouseover="addLine('house')"><img src="/imagesForThemes/house.svg" alt=""><span>House</span></div>
            <div id="plantsTheme" @mouseover="addLine('plant')"><img src="/imagesForThemes/plants.svg" alt=""><span>Plants</span></div>
            <div id="spaceTheme" @mouseover="addLine('space')"><img src="/imagesForThemes/space.svg" alt=""><span>Space</span></div>        
            <div id="transportationTheme" @mouseover="addLine('transportation')"><img src="/imagesForThemes/transportation.svg" alt=""><span>Transportation</span></div>
            <div id="waterTheme" @mouseover="addLine('water')"><img src="/imagesForThemes/water.svg" alt=""><span>Water</span></div>
            <div id="worldCultureTheme" @mouseover="addLine('worldCulture')"><img src="/imagesForThemes/worldCulture.svg" alt=""><span>World</span></div>
            <div id="bodyLine"></div>
            <div id="colorLine"></div>
            <div id="fallLine"></div>
            <div id="geographyLine"></div>
            <div id="houseLine"></div>
            <div id="plantLine"></div>
            <div id="spaceLine"></div>
            <div id="transportationLine"></div>
            <div id="waterLine"></div>
            <div id="worldCultureLine"></div>
            <div id="coverLine"></div>

            <div id="fourChoices"></div>
        </div>
        
        <div id="fourUnitsContainer">
            <figure>
                <img id="unitImage1" class='unitImage' src="https://circle-eld.s3.us-east-2.amazonaws.com/1606773191058" alt="">
                <figcaption>Unit 1</figcaption>
                
                <div id="vocabContainer1" class='vocabContainer'>
                <span id='unit1vocab1' class='unitVocab'>brain</span>
                <span id='unit1vocab2' class='unitVocab'>chest</span>
                <span id='unit1vocab3' class='unitVocab'>head</span>
                <span id='unit1vocab4' class='unitVocab'>knee</span>
                <span id='unit1vocab5' class='unitVocab'>muscle</span>
                </div>
            </figure>
            <figure>
                <img id="unitImage2" src="https://circle-eld.s3.us-east-2.amazonaws.com/1605900798726" alt="">
                <figcaption>Unit 2</figcaption>
                
                <div id="vocabContainer1" class='vocabContainer'>
                <span id='unit2vocab1' class='unitVocab'>arm</span>
                <span id='unit2vocab2' class='unitVocab'>back</span>
                <span id='unit2vocab3' class='unitVocab'>hair</span>
                <span id='unit2vocab4' class='unitVocab'>finger</span>
                <span id='unit2vocab5' class='unitVocab'>neck</span>
                </div>
            </figure>
            <figure>
                <img id="unitImage3" src="https://circle-eld.s3.us-east-2.amazonaws.com/1606772503460" alt="">
                <figcaption>Unit 3</figcaption>
                
                <div id="vocabContainer1" class='vocabContainer'>
                <span id='unit3vocab1' class='unitVocab'>bone</span>
                <span id='unit3vocab2' class='unitVocab'>eyebrow</span>
                <span id='unit3vocab3' class='unitVocab'>heart</span>
                <span id='unit3vocab4' class='unitVocab'>mouth</span>
                <span id='unit3vocab5' class='unitVocab'>tongue</span>
                </div>
            </figure>
            <figure>
                <img id="unitImage4" src="https://circle-eld.s3.us-east-2.amazonaws.com/1605899427223" alt="">
                <figcaption>Unit 4</figcaption>
                
                <div id="vocabContainer1" class='vocabContainer'>
                <span id='unit4vocab1' class='unitVocab'>eye</span>
                <span id='unit4vocab2' class='unitVocab'>leg</span>
                <span id='unit4vocab3' class='unitVocab'>ear</span>
                <span id='unit4vocab4' class='unitVocab'>nose</span>
                <span id='unit4vocab5' class='unitVocab'>toes</span>
                </div>
            </figure>
        </div>
    </div>
</template>

<script>
export default {
    async asyncData({ $axios }) {
    try {
      let response = await $axios.$get("http://localhost:3000/api/products");
    //   console.log(response.products);
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
    if (theme == "plant") {theme += "s"};
    
    return {
      unit: unit,
      theme: theme,
      title: "Themes and Units",
    }
  },

  created () {
    const title = this.title;
    if (title) {
      try {
        document.title = title
      } catch {
        // console.log("title mia")
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
    addLine(theme) {
        let unit1vocab1 = document.getElementById("unit1vocab1");
        let unit1vocab2 = document.getElementById("unit1vocab2");
        let unit1vocab3 = document.getElementById("unit1vocab3");
        let unit1vocab4 = document.getElementById("unit1vocab4");
        let unit1vocab5 = document.getElementById("unit1vocab5");

        let unit2vocab1 = document.getElementById("unit2vocab1");
        let unit2vocab2 = document.getElementById("unit2vocab2");
        let unit2vocab3 = document.getElementById("unit2vocab3");
        let unit2vocab4 = document.getElementById("unit2vocab4");
        let unit2vocab5 = document.getElementById("unit2vocab5");

        let unit3vocab1 = document.getElementById("unit3vocab1");
        let unit3vocab2 = document.getElementById("unit3vocab2");
        let unit3vocab3 = document.getElementById("unit3vocab3");
        let unit3vocab4 = document.getElementById("unit3vocab4");
        let unit3vocab5 = document.getElementById("unit3vocab5");

        let unit4vocab1 = document.getElementById("unit4vocab1");
        let unit4vocab2 = document.getElementById("unit4vocab2");
        let unit4vocab3 = document.getElementById("unit4vocab3");
        let unit4vocab4 = document.getElementById("unit4vocab4");
        let unit4vocab5 = document.getElementById("unit4vocab5");

        let vocabs = [unit1vocab1, unit1vocab2, unit1vocab3, unit1vocab4, unit1vocab5, unit2vocab1,unit2vocab2,unit2vocab3,unit2vocab4,unit2vocab5, unit3vocab1,unit3vocab2,unit3vocab3,unit3vocab4,unit3vocab5,unit4vocab1,unit4vocab2,unit4vocab3,unit4vocab4,unit4vocab5]

        for (let i = 0; i < 400; i += 40) {
            if (this.products[i].theme == theme) {
                for (let j = 0; j < 20; j++) {
                    vocabs[j].innerText = this.products[i + (j*2)].vocabulary;
                }
            }
            if (this.products[i].theme == "plants") {
                for (let j = 0; j < 20; j++) {
                    vocabs[j].innerText = this.products[i + (j*2)].vocabulary;
                }
            } 
        }

        let displayLines = [
            document.getElementById("bodyLine"),
            document.getElementById("colorLine"),
            document.getElementById("fallLine"),
            document.getElementById("geographyLine"),
            document.getElementById("houseLine"),
            document.getElementById("plantLine"),
            document.getElementById("spaceLine"),
            document.getElementById("transportationLine"),
            document.getElementById("waterLine"),
            document.getElementById("worldCultureLine"),
        ]

        for (let i = 0; i < displayLines.length; i++) {
            displayLines[i].style.visibility = "hidden";
        }

        let displayLine = document.getElementById(theme + "Line");
        displayLine.style.visibility = "visible";

        let image1 = document.getElementById("unitImage1");
        let image2 = document.getElementById("unitImage2");
        let image3 = document.getElementById("unitImage3");
        let image4 = document.getElementById("unitImage4");

        let sources = {
            "body1":"https://circle-eld.s3.us-east-2.amazonaws.com/1606773191058",
            "body2":"https://circle-eld.s3.us-east-2.amazonaws.com/1605900798726",
            "body3":"https://circle-eld.s3.us-east-2.amazonaws.com/1606772503460",
            "body4":"https://circle-eld.s3.us-east-2.amazonaws.com/1605899427223",

            "color1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607094713744",
            "color2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607273000564",
            "color3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607273125499",
            "color4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607273414308",

            "fall1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607273845235",
            "fall2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607273991595",
            "fall3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607274420646",
            "fall4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607274533908",

            "geography1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607355264157",
            "geography2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607355435084",
            "geography3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607355785494",
            "geography4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607356090111",

            "house1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607357340545",
            "house2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607358036847",
            "house3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607358223929",
            "house4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607364743216",
            
            "plant1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607365413734",
            "plant2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607365860146",
            "plant3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607366633592",
            "plant4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607367002081",

            "space1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607367187748",
            "space2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607367597398",
            "space3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607367733647",
            "space4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607367977818",

            "transportation1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607368829689",
            "transportation2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607369541702",
            "transportation3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607371363450",
            "transportation4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607372040299",

            "water1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607372811888",
            "water2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607373167285",
            "water3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607373508510",
            "water4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607373749274",

            "worldCulture1":"https://circle-eld.s3.us-east-2.amazonaws.com/1607374148280",
            "worldCulture2":"https://circle-eld.s3.us-east-2.amazonaws.com/1607374262772",
            "worldCulture3":"https://circle-eld.s3.us-east-2.amazonaws.com/1607374883268",
            "worldCulture4":"https://circle-eld.s3.us-east-2.amazonaws.com/1607375461336",
        }
        
        image1.src = sources[theme + "1"];
        image2.src = sources[theme + "2"];
        image3.src = sources[theme + "3"];
        image4.src = sources[theme + "4"];

        image1.onclick = function () {window.open ('workSelector?theme=' + theme + '&unit=1', '_self',false)};
        image2.onclick = function () {window.open ('workSelector?theme=' + theme + '&unit=2', '_self',false)};
        image3.onclick = function () {window.open ('workSelector?theme=' + theme + '&unit=3', '_self',false)};
        image4.onclick = function () {window.open ('workSelector?theme=' + theme + '&unit=4', '_self',false)};
    },
    backToMain() {
        window.open ('main','_self',false)
    },
  }
};
</script>

<style>

/* @import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap'); */


body {
    background-color: lightcyan;
    /* font-family: 'Lato', sans-serif; */
}



figcaption {
    background-color:rgb(75, 221, 139);
    border-right: 2px solid darkgreen;
    border-bottom: 2px solid darkgreen;
    border-left: 2px solid darkgreen;
    border-top: 10px solid salmon;
    border-radius: 5px;
    margin: 4px;
}

.unitVocab {
    background-color: lavender;
    border: 4px solid salmon;
    margin: 4px;
    padding: 3px;
    border-radius: 10px;
    width: 200px;
    transform: translateX(16%);
}


#span1 {
    position: absolute;
    top: 0px;
    left: 25px;
    cursor: pointer;
}


#curriculumHeader {
    font-size: 4.1em;
    animation: none;
}

#whatToDo {
    font-size: 2em;
    width: 100%;
}


#allImagesContainer > span > img{
    visibility: hidden;
}

#designOptionsBar {
    visibility: hidden;
}

#curriculumOptionsBar {
    visibility: hidden;
}

#aboutSandyOptionsBar {
    visibility: hidden;
}

#contactOptionsBar {
    visibility: hidden;
}

img+span {
    font-size: 1.2rem;
}

#bodyTheme:hover, #colorTheme:hover, #fallTheme:hover, #geographyTheme:hover, #houseTheme:hover, #plantsTheme:hover, #spaceTheme:hover, #transportationTheme:hover, #waterTheme:hover, #worldCultureTheme:hover{
    transform: translateY(-5%);
}

figure {
    text-align: center;
}

figcaption {
    font-size: 1.2rem;
}

#fourUnitsContainer {
    display:flex;
    align-items: center;
    justify-items: center;
    align-content: center;
    justify-content: center;
    transform: translateY(-78%);
}

@keyframes showSelf {
    0% {border-radius: 80px;}
    100% {border-radius: 10px;}
}

#fourUnitsContainer > figure > img:hover {
    cursor: pointer;
    animation: showSelf 375ms forwards;
}

#fourUnitsContainer > figure > img {
    object-fit: cover;
    width: 250px;
    height: 200px;
    margin: 10px;
    border-radius: 80px;
}

#bodyLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 1;
    height: 200px;
    width: 0px;
    grid-row: 2;
    transform: rotate(-60deg) translateY(18px) translateX(130px);
    visibility: visible;
}

#colorLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 2;
    height: 175px;
    width: 0px;
    grid-row: 2;
    transform: rotate(-55deg) translateY(-8px) translateX(122px);
    visibility: hidden;
}

#fallLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 3;
    height: 140px;
    width: 0px;
    grid-row: 2;
    transform: rotate(-45deg) translateY(-45px) translateX(104px);
    visibility: hidden;
}

#geographyLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 4;
    height: 120px;
    width: 0px;
    grid-row: 2;
    transform: rotate(-30deg) translateY(-80px) translateX(76px);
    visibility: hidden;
}

#houseLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 5;
    height: 110px;
    width: 0px;
    grid-row: 2;
    transform: rotate(-15deg) translateY(-104px) translateX(34px);
    visibility: hidden;
}

#plantLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 6;
    height: 110px;
    width: 0px;
    grid-row: 2;
    transform: rotate(15deg) translateY(-104px) translateX(-48px);
    visibility: hidden;
}

#spaceLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 7;
    height: 120px;
    width: 0px;
    grid-row: 2;
    transform: rotate(30deg) translateY(-72px) translateX(-90px);
    visibility: hidden;
}

#transportationLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 8;
    height: 140px;
    width: 0px;
    grid-row: 2;
    transform: rotate(45deg) translateY(-25px) translateX(-124px);
    visibility: hidden;
}

#waterLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 9;
    height: 170px;
    width: 0px;
    grid-row: 2;
    transform: rotate(55deg) translateY(0px) translateX(-122px);
    visibility: hidden;
}

#worldCultureLine {
    background-color: darkgreen;
    border-left: 4px solid salmon;
    border-right: 4px solid salmon;
    grid-column: 10;
    height: 200px;
    width: 0px;
    grid-row: 2;
    transform: rotate(60deg) translateY(20px) translateX(-130px);
    visibility: hidden;
}

#coverLine {
    border-top: 15px solid darkgreen;
    background-color: salmon;
    grid-column: 3 / 9;
    height: 0px;
    width: 200%;
    grid-row: 3;
    transform: translateY(-265px);
}

div > img {
    height: 60px;
    align-self: center;
}

div > span {
    display: block;
    text-align: center;
}

#themeContainer {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    justify-items: center;
    align-items: center;
}

#themeContainer > div {
    margin-bottom: 8px;
    padding: 10px;
    display: block;
}

#themeContainer > div:hover {
    cursor: s-resize;
}

#bodyTheme {
    grid-column: 1 / 2;
}

#colorTheme {
    grid-column: 2 / 3;
}

#fallTheme {
    grid-column: 3 / 4;
}

#geographyTheme {
    grid-column: 4 / 5;
}

#houseTheme {
    grid-column: 5 / 6;
}

#plantsTheme {
    grid-column: 6 / 7;
}

#spaceTheme {
    grid-column: 7 / 8;
}

#transportationTheme {
    grid-column: 8 / 9;
}

#waterTheme {
    grid-column: 9 / 10;
}

#worldCultureTheme {
    grid-column: 10 / 11;
}

#optionsBar {
    display: flex;
    background-color: rgb(75, 221, 139);
    height: 43px;
}

#optionsBar > div > span {
    font-size: 1.2rem;
    background-color: rgb(250, 195, 189);
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}

#logoFinal {
  height: 70px; 
  margin-top: 5px;
  border-radius: 5px;
}

#navbar {
    display: flex;
    justify-items: center;
    align-items: center;
    background-color: salmon;
    border-bottom: 2px solid darkgreen;
}

#navbar > span {
    margin: auto;
    background: salmon;
    color: black;
    padding: 9px;
    border-radius: 5px;
}
#logoFinal:hover {cursor: pointer;
    background-color: rgb(211, 107, 96);
}

</style>