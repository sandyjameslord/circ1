<template>
    <div>
        <span id="topText">For Classes and Individuals</span>
        <span id="bottomText">Extensions for Language Development</span>
        <img id='newLogo' src="/newerLogo.png" alt="">
        <span> making changes: 3 </span>
        <div class='imageCreator' v-for="(product, index) in products" :key="product._id">
            <div v-if="(index < 36)">
                <img class="frame" :id=index :src="product.photo">         
            </div>
        </div>
        <div>
            <span @click="bringToCenter()" id="entry">CIRCLE-ELD</span>
        </div>
    </div>
</template>

<script>
export default {
    async asyncData({ $axios }) {
        try {
            let response = await $axios.$get("/api/products");
            return {
                // products: [{'id':1, 'sentence':"first thing that comes to mind"}]
                products: response.products
            }
        } catch (err) {
            console.log(err)
        }
    },
    methods: {
        bringToCenter() {
            let upperText = document.getElementById("topText");
            upperText.style.visibility = "visible";  
            let lowerText = document.getElementById("bottomText");
            lowerText.style.visibility = "visible";

            let images = document.getElementsByClassName("frame");
            for (let i = 0; i < images.length; i++){

                let currentImage = images[i];
                let coords = currentImage.getBoundingClientRect();
                let width = coords.right - coords.left;
                let height = width;
                let kf = "@keyframes allToCenter" + i + " { 0% { border-width: 20px; position: absolute; height: " + height + "px; width: " + width +"px;  left: " + coords.left + "px; top: " + coords.top + "px; } 100% { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%);}} ";
                console.log(kf);
                document.styleSheets[0].insertRule(kf);

                currentImage.style.animation += "allToCenter" + i + " 5s ease-out forwards";
            }
            setTimeout(function() {
                window.open ('main','_self',false)
            }, 8000);
        },
    }
};
</script>

<style>

/* @import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900;&display=swap'); */

body {
    background: lightcyan;
    /* font-family: 'Lato', sans-serif; */
}

#newLogo {
    position: fixed;
    top: 50%;
    left: 50%;
    opacity: 0;
    transform: translate(-50%, -50%);
    height: 220px;
    width: 290px;
    z-index: 50;
    background-color: black;
    border-radius: 10px;
}

@keyframes moveLogoToCorner {
    0% {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%) scale(1); 
    }
    100% {
        position: fixed;
        top: 5%;
        left: 7%;
        transform: translate(-50%, -50%) scale(0.33); 
    }
}

#topText {
    visibility: visible;
    font-size: 2rem;
    text-align: center;
    background-color: lavender;
    overflow: hidden;
    white-space: nowrap;
    border: 8px solid salmon;
    padding-left: 10px;
    padding-right: 10px;
    border-radius: 10px;
    visibility: hidden;
}

#bottomText {
    visibility: visible;
    font-size: 3rem;
    text-align: center;
    background-color: lavender;
    overflow: hidden;
    white-space: nowrap;
    border: 8px solid salmon;
    padding-left: 10px;
    padding-right: 10px;
    border-radius: 10px;
    visibility: hidden;
}

#entry {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%); 
    background-color: lavender;
    border: 3px solid salmon;
    font-size: 3rem;
    padding: 5px;
    border-radius: 10px;
    white-space: pre;
    width: 284px;  
    height: 73px;
    z-index: 4000000;
}

#topText {
    position: fixed;
    top: 75%;
    left: 50%;
    transform: translate(-50%, -50%);
}

#bottomText {
    position: fixed;
    top: 25%;
    left: 50%;
    transform: translate(-50%, -50%);
}


.imageCreator:nth-child(n) > div > img {
    object-fit: cover;
    border-radius: 50%;
    border: 7px solid lightcyan;
}

.imageCreator:nth-child(1) > div > img {
    border-color: lightgoldenrodyellow;
    position: absolute;
    left: 30%;
    top: 30%;
    width: 200px;
    height: 200px;
    animation: getBigAndSmall1 10000ms linear infinite forwards;
}

.imageCreator:nth-child(2) > div > img {
    border-color: lightgreen;
    position: absolute;
    left: 10%;
    top: 40%;
    width: 190px;
    height: 190px;
    animation: getBigAndSmall2 8000ms linear infinite forwards;
}

.imageCreator:nth-child(3) > div > img {
    border-color: lightgrey;
    position: absolute;
    left: 50%;
    top: 10%;
    width: 180px;
    height: 180px;
    animation: getBigAndSmall3 11000ms linear infinite forwards;
}

.imageCreator:nth-child(4) > div > img {
    border-color: lightcoral;
    position: absolute;
    left: 30%;
    top: 10%;
    width: 170px;
    height: 170px;
    animation: getBigAndSmall4 13000ms linear infinite forwards;
}

.imageCreator:nth-child(5) > div > img {
    border-color: lightpink;
    position: absolute;
    left: 20%;
    top: 60%;
    width: 160px;
    height: 160px;
    animation: getBigAndSmall5 12000ms linear infinite forwards;
}

.imageCreator:nth-child(6) > div > img {
    border-color: lightseagreen;
    position: absolute;
    left: 10%;
    top: 30%;
    width: 150px;
    height: 150px;
    animation: getBigAndSmall6 11000ms linear infinite forwards;
}

.imageCreator:nth-child(7) > div > img {
    border-color: lightsalmon;
    position: absolute;
    left: 40%;
    top: 20%;
    width: 140px;
    height: 140px;
    animation: getBigAndSmall7 14000ms linear infinite forwards;
}

.imageCreator:nth-child(8) > div > img {
    border-color: sandybrown;
    position: absolute;
    left: 50%;
    top: 20%;
    width: 130px;
    height: 130px;
    animation: getBigAndSmall8 11000ms linear infinite forwards;
}

.imageCreator:nth-child(9) > div > img {
    border-color: seagreen;
    position: absolute;
    left: 60%;
    top: 60%;
    width: 120px;
    height: 120px;
    animation: getBigAndSmall1 16000ms linear infinite forwards;
}

.imageCreator:nth-child(10) > div > img {
    border-color: lavender;
    position: absolute;
    left: 70%;
    top: 70%;
    width: 110px;
    height: 110px;
    animation: getBigAndSmall2 12000ms linear infinite forwards;
}

.imageCreator:nth-child(11) > div > img {
    border-color: lavenderblush;
    position: absolute;
    left: 60%;
    top: 50%;
    width: 100px;
    height: 100px;
    animation: getBigAndSmall3 12000ms linear infinite forwards;
}

.imageCreator:nth-child(12) > div > img {
    border-color: lemonchiffon;
    position: absolute;
    left: 60%;
    top: 60%;
    width: 90px;
    height: 90px;
    animation: getBigAndSmall4 11000ms linear infinite forwards;
}

.imageCreator:nth-child(13) > div > img {
    border-color: goldenrod;
    position: absolute;
    left: 30%;
    top: 70%;
    width: 80px;
    height: 80px;
    animation: getBigAndSmall5 9000ms linear infinite forwards;
}

.imageCreator:nth-child(14) > div > img {
    border-color: firebrick;
    position: absolute;
    left: 50%;
    top: 30%;
    width: 70px;
    height: 70px;
    animation: getBigAndSmall6 14000ms linear infinite forwards;
}

.imageCreator:nth-child(15) > div > img {
    border-color: wheat;
    position: absolute;
    left: 50%;
    top: 40%;
    width: 60px;
    height: 60px;
    animation: getBigAndSmall7 10000ms linear infinite forwards;
}

.imageCreator:nth-child(16) > div > img {
    border-color: palegreen;
    position: absolute;
    left: 50%;
    top: 50%;
    width: 50px;
    height: 50px;
    animation: getBigAndSmall8 11000ms linear infinite forwards;
}

.imageCreator:nth-child(17) > div > img {
    border-color: navy;
    position: absolute;
    left: 50%;
    top: 60%;
    width: 40px;
    height: 40px;
    animation: getBigAndSmall1 11000ms linear infinite forwards;
}

.imageCreator:nth-child(18) > div > img {
    border-color: teal;
    position: absolute;
    left: 50%;
    top: 70%;
    width: 30px;
    height: 30px;
    animation: getBigAndSmall2 11000ms linear infinite forwards;
}

.imageCreator:nth-child(19) > div > img {
    border-color: thistle;
    position: absolute;
    left: 80%;
    top: 30%;
    width: 50px;
    height: 50px;
    animation: getBigAndSmall3 13000ms linear infinite forwards;
}

.imageCreator:nth-child(20) > div > img {
    border-color: rebeccapurple;
    position: absolute;
    left: 80%;
    top: 40%;
    width: 40px;
    height: 40px;
    animation: getBigAndSmall4 12000ms linear infinite forwards;
}

.imageCreator:nth-child(21) > div > img {
    border-color: lightgoldenrodyellow;
    position: absolute;
    left: 80%;
    top: 50%;
    width: 100px;
    height: 100px;
    animation: getBigAndSmall5 11000ms linear infinite forwards;
}

.imageCreator:nth-child(22) > div > img {
    border-color: lightgreen;
    position: absolute;
    left: 80%;
    top: 60%;
    width: 90px;
    height: 90px;
    animation: getBigAndSmall6 12000ms linear infinite forwards;
}

.imageCreator:nth-child(23) > div > img {
    border-color: lightgrey;
    position: absolute;
    left: 60%;
    top: 70%;
    width: 80px;
    height: 80px;
    animation: getBigAndSmall7 11000ms linear infinite forwards;
}

.imageCreator:nth-child(24) > div > img {
    border-color: lightcoral;
    position: absolute;
    left: 70%;
    top: 30%;
    width: 70px;
    height: 70px;
    animation: getBigAndSmall8 13000ms linear infinite forwards;
}

.imageCreator:nth-child(25) > div > img {
    border-color: lightpink;
    position: absolute;
    left: 70%;
    top: 40%;
    width: 60px;
    height: 60px;
    animation: getBigAndSmall1 10000ms linear infinite forwards;
}

.imageCreator:nth-child(26) > div > img {
    border-color: lightseagreen;
    position: absolute;
    left: 70%;
    top: 50%;
    width: 50px;
    height: 50px;
    animation: getBigAndSmall2 9000ms linear infinite forwards;
}

.imageCreator:nth-child(27) > div > img {
    border-color: lightsalmon;
    position: absolute;
    left: 70%;
    top: 30%;
    width: 40px;
    height: 40px;
    animation: getBigAndSmall3 10000ms linear infinite forwards;
}

.imageCreator:nth-child(28) > div > img {
    border-color: sandybrown;
    position: absolute;
    left: 70%;
    top: 50%;
    width: 100px;
    height: 100px;
    animation: getBigAndSmall4 11000ms linear infinite forwards;
}

.imageCreator:nth-child(29) > div > img {
    border-color: seagreen;
    position: absolute;
    left: 10%;
    top: 10%;
    width: 90px;
    height: 90px;
    animation: getBigAndSmall5 12000ms linear infinite forwards;
}

.imageCreator:nth-child(30) > div > img {
    border-color: lavender;
    position: absolute;
    left: 10%;
    top: 50%;
    width: 80px;
    height: 80px;
    animation: getBigAndSmall6 14000ms linear infinite forwards;
}

.imageCreator:nth-child(31) > div > img {
    border-color: lavenderblush;
    position: absolute;
    left: 10%;
    top: 90%;
    width: 70px;
    height: 70px;
    animation: getBigAndSmall7 11000ms linear infinite forwards;
}

.imageCreator:nth-child(32) > div > img {
    border-color: lemonchiffon;
    position: absolute;
    left: 90%;
    top: 10%;
    width: 60px;
    height: 60px;
    animation: getBigAndSmall8 9000ms linear infinite forwards;
}

.imageCreator:nth-child(33) > div > img {
    border-color: goldenrod;
    position: absolute;
    left: 90%;
    top: 15%;
    width: 50px;
    height: 50px;
    animation: getBigAndSmall1 11000ms linear infinite forwards;
}

.imageCreator:nth-child(34) > div > img {
    border-color: firebrick;
    position: absolute;
    left: 90%;
    top: 20%;
    width: 40px;
    height: 40px;
    animation: getBigAndSmall2 10000ms linear infinite forwards;
}

.imageCreator:nth-child(35) > div > img {
    border-color: wheat;
    position: absolute;
    left: 50%;
    top: 30%;
    width: 70px;
    height: 70px;
    animation: getBigAndSmall3 14000ms linear infinite forwards;
}

.imageCreator:nth-child(36) > div > img {
    border-color: palegreen;
    position: absolute;
    left: 25%;
    top: 25%;
    width: 60px;
    height: 60px;
    animation: getBigAndSmall4 12000ms linear infinite forwards;
}

.imageCreator:nth-child(37) > div > img {
    border-color: navy;
    position: absolute;
    left: 75%;
    top: 50%;
    width: 50px;
    height: 50px;
    animation: getBigAndSmall5 13000ms linear infinite forwards;
}

.imageCreator:nth-child(38) > div > img {
    border-color: teal;
    position: absolute;
    left: 75%;
    top: 50%;
    width: 40px;
    height: 40px;
    animation: getBigAndSmall6 11000ms linear infinite forwards;
}

.imageCreator:nth-child(39) > div > img {
    border-color: thistle;
    position: absolute;
    left: 25%;
    top: 75%;
    width: 50px;
    height: 50px;
    animation: getBigAndSmall7 11000ms linear infinite forwards;
}

.imageCreator:nth-child(40) > div > img {
    border-color: rebeccapurple;
    position: absolute;
    left: 60%;
    top: 42%;
    width: 40px;
    height: 40px;
    animation: getBigAndSmall8 12000ms linear infinite forwards;
} 

@keyframes getBigAndSmall1 {
    0% {transform: scale(1) translate(10px, 10px);}
    25% {transform: scale(2) translate(30px, 30px);}
    50% {transform: scale(3) translate(50px, 50px);}
    75% {transform: scale(2) translate(30px, 30px);}
    100% {transform: scale(1) translate(10px, 10px);}
}

@keyframes getBigAndSmall2 {
    0% {transform: scale(1) translate(-10px, 10px);}
    25% {transform: scale(2) translate(-30px, 30px);}
    50% {transform: scale(3) translate(-50px, 50px);}
    75% {transform: scale(2) translate(-30px, 30px);}
    100% {transform: scale(1) translate(-10px, 10px);}
}

@keyframes getBigAndSmall3 {
    0% {transform: scale(2) translate(10px, 10px);}
    25% {transform: scale(4) translate(50px, 50px);}
    50% {transform: scale(6) translate(90px, 90px);}
    75% {transform: scale(4) translate(50px, 50px);}
    100% {transform: scale(2) translate(10px, 10px);}
}

@keyframes getBigAndSmall4 {
    0% {transform: scale(2) translate(-10px, 30px);}
    25% {transform: scale(4) translate(-50px, 0px);}
    50% {transform: scale(6) translate(-90px, -30px);}
    75% {transform: scale(4) translate(-50px, 0px);}
    100% {transform: scale(2) translate(-10px, 30px);}
}

@keyframes getBigAndSmall5 {
    0% {transform: scale(1) translate(30px, 10px);}
    25% {transform: scale(2) translate(30px, 30px);}
    50% {transform: scale(3) translate(30px, 50px);}
    75% {transform: scale(2) translate(30px, 30px);}
    100% {transform: scale(1) translate(30px, 10px);}
}

@keyframes getBigAndSmall6 {
    0% {transform: scale(1) translate(-70px, 10px);}
    25% {transform: scale(2) translate(-70px, 30px);}
    50% {transform: scale(3) translate(-70px, 50px);}
    75% {transform: scale(2) translate(-70px, 30px);}
    100% {transform: scale(1) translate(-70px, 10px);}
}

@keyframes getBigAndSmall7 {
    0% {transform: scale(2) translate(10px, 50px);}
    25% {transform: scale(4) translate(50px, 50px);}
    50% {transform: scale(6) translate(90px, 50px);}
    75% {transform: scale(4) translate(50px, 50px);}
    100% {transform: scale(2) translate(10px, 50px);}
}

@keyframes getBigAndSmall8 {
    0% {transform: scale(2) translate(0px, 10px);}
    25% {transform: scale(4) translate(0px, 50px);}
    50% {transform: scale(6) translate(0px, 90px);}
    75% {transform: scale(4) translate(0px, 50px);}
    100% {transform: scale(2) translate(0px, 10px);}
}

#entry:hover {
    cursor: pointer;
}

</style>