<template>
    <div>
        <div id="navbar">
            <span id='span1'><img @click="openCurriculum()" id='logoFinal' src="/circleLOGO.png" alt=""></span>
            <span @mouseover="addText('curriculum')" id="curriculumSpan">How to Use</span>
            <span @mouseover="addText('design')" id="designSpan">Inspiration and Design</span>
            <span @mouseover="addText('aboutSandy')" id="sandyLordSpan">About the Designer</span>
            <span @mouseover="addText('contact')" id="contactSpan">Contact</span>
        </div>

        <div id="optionsBar">
            <div id="designOptionsBar">
                <span @click="showPage('design')">Design</span>
                <span @click="showPage('inspiration')">Inspiration</span>
            </div>
            <div id="curriculumOptionsBar">
                <span @click="showPage('student')">In Small Group</span>
                <span @click="showPage('teacher')">By Yourself</span>
            </div>
            <div id="aboutSandyOptionsBar">
                <span @click="showPage('softwareDeveloperLinguistEducator')">Software Developer</span>
                <span @click="showPage('softwareDeveloperLinguistEducator')">Linguist</span>
                <span @click="showPage('softwareDeveloperLinguistEducator')">Educator</span>
            </div>
            <div id="contactOptionsBar">
                <span @click="showPage('contact')">Contact</span>
            </div>
        </div>

        <div id="curriculumContainer">
            <div id="studentCurriculum">
                <p id="studentCurriculumInfo1">Small Group</p>
                <img id='studentsImg' src="/students.png" alt="">
                <img id='teacherImg' src="/teacher.png" alt="">
                <img id='explainImg1' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373740099" alt="">
                <img id='explainImg2' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1606773315833" alt="">
                <img id='explainImg3' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1606772984915" alt="">
                <img id='explainImg4' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607374530701" alt="">
                <img id='explainImg5' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607355264157" alt="">
                <img id='explainImg6' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607368906998" alt="">
                <img id='explainImg7' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373472112" alt="">
                <img id='explainImg8' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607357615625" alt="">
                <img id='explainImg9' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373921147" alt="">
                <img id='explainImg10' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373740099" alt="">
                <img id='explainImg11' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607367762877" alt="">
                <img id='explainImg12' class='explain' src="https://circle-eld.s3.us-east-2.amazonaws.com/1607274719496" alt="">

                <img id='arrow1' class='arrows' src="/arrows.png" alt="">        
                <img id='arrow2' class='arrows' src="/arrows.png" alt="">   
                <img id='arrow3' class='arrows' src="/arrows2.png" alt="">    
                <p class='share' id="see">See</p>
                <p class='share' id="listen">Listen</p>
                <p class='share' id="know">Know</p>
                <p class='share' id="connect">Connect</p>
                <p class='share' id="remember">Question</p>
                <p class='share' id="question">Remember</p>
                <span class='closer' id='studentWindowCloser' @click="closePage('student')">X</span>
                
            </div> 
            <div id="teacherCurriculum">
                <p id="teacherCurriculumInfo1">By Yourself</p>                           
                <span class='closer' id='teacherWindowCloser' @click="closePage('teacher')">X</span>
                <img id='selectionForStudent' src="/selectionsForStudent.png" alt="" @click="openCurriculum()">
                <span id="clickAndPractice">Choose a theme and select an extension.Look at the images and try the words. Ask questions and make observations. Enjoy!</span>
                
            </div>
            <div id="parentCurriculum">
                <p id="parentCurriculumInfo1">Parents and Caregivers</p>                                
                <span class='closer' id='parentWindowCloser' @click="closePage('parent')">X</span>
            </div>
            <div id="designPage">
                <p id="designInfo1">Design</p>  
                <span id='designInfoA'>Originally designed as an Elementary English Learners classroom curriculum, CIRCLE-ELD promotes language development for all. </span>
                <span id='designInfoB'>With multiple ways to access information, from visual to audio, from contextualized, preformed, acedmic questions to the ability to make and listen to a student's own verbal expressions, CIRCLE-ELD is a powerful extension for any student.</span>
                <span id='designInfoC'>Designed and implemented in the classroom, with constant feedback from students, parents, fellow teachers and administration, CIRCLE-ELD has been used with hundreds of elementary students and helped them feel comfortable with language as they grow academic skills. </span>                             
                <span class='closer' id='designWindowCloser' @click="closePage('design')">X</span>
            </div>
            <div id='processPage'>
                <p id="processInfo1">Process</p>                               
                <span class='closer' id='processWindowCloser' @click="closePage('process')">X</span>
            </div>
            <div id='inspirationPage'>
                <p id="inspirationInfo1">Inspiration</p>
                <span id='inspirationInfoA'>As an Elementary ESL teacher with over 50 students seen daily, Sandy Lord was looking for a curriculum where he could have maximum impact from both an academic and linguistic perspective. Young students, especially English Learners, need lots of context to learn both language and knowledge. However, even without either of those skills, everyone still wants to express themselves and be part of a group, as long as they are comfortable.</span>
                <span id='inspirationInfoB'>Sandy designed CIRCLE-ELD (formerly called CIRCLE-ELL) to be the gateway for acceptance into a linguistic community. With communication rather than competence the goal, students, regardless of English competency, felt free to express what they could, and their skills progressed rapidly. Sandy was given the 2014 Anne Dow Award from MATSOL for this work. The curriculum has expanded since then, and is now represented in this web app, published January, 2021.</span>                                      
                <span class='closer' id='inspirationWindowCloser' @click="closePage('inspiration')">X</span>
            </div>

            <div id="softwareDeveloperLinguistEducator">
                <p id="softwareDeveloperLinguistEducatorInfo1">Software Engineer, Linguist and Educator: Sandy Lord</p>
                <span id="educatorInfo1">Sandy Lord is the Software Engineer, Linguist and Educator behind CIRCLE-ELD. Sandy is a former Elementary ESL Teacher in Massachusetts Public School systems in Taunton, Burlington, and Worcester. Prior to becomming an elementary teacher, Sandy taught as an adjunct professor at Brandeis University and Northeastern University. He received his Masters in Applied Linguistics from Boston University and was a Teaching Fellow for 5 semesters in the Intro to Linguistics Class. Sandy received the 2014 Anne Dow Award from MATSOL for his work on CIRCLE-ELD. Entering the Software Engineering field in 2018, Sandy is fluent in Python, JavaScript, HTML, CSS, UNIX, Java, and others. In addition to self-teaching, he has now taken 7 Computer Science courses at Framingham State University, including:</span>
                <span id='coursesTaken'>Java I, Java II, Python, WebDev with JS/HTML/CSS, UNIX and OS, Data Structures, and Database Management</span>
                <span id='sandyJobInterest'>As a Software Engineer, Linguist or Educator, Sandy is looking to work on a team where he can apply any of his skills. Please contact with any information.</span>                               
                <span class='closer' id='educatorWindowCloser' @click="closePage('softwareDeveloperLinguistEducator')">X</span>
            </div>
            <div id='linguistPage'>
                <p id="linguistInfo1">Linguist</p>                               
                <span class='closer' id='linguistWindowCloser' @click="closePage('softwareDeveloperLinguistEducator')">X</span>
            </div>
            <div id='softwareDeveloperPage'>
                <p id="softwareDeveloperInfo1">Software Developer</p>                               
                <span class='closer' id='softwareDeveloperWindowCloser' @click="closePage('softwareDeveloperLinguistEducator')">X</span>
            </div>
            <div id='contactPage'>
                <p id="contactInfo1">Contact</p>
                <p id="sandyLord">Sandy Lord</p>
                <p id='emailName'>email: sandylord.dev@gmail.com</p>
                <p id='linkedIn'>LinkedIn: /sandy-lord-engineer</p>
                <p id='gitHub'>GitHub: /sandyjameslord</p>
                <img id='sandyImage1' src="/sandylord.jpg" alt="">                                  

                <span class='closer' id='contactWindowCloser' @click="closePage('contact')">X</span>
            </div>
        </div>

        <div id="mainDisplay">
            <div id="centerDisplay">
                
                <div id='firstSentence'>Click on an image  - or <span style="cursor:pointer;" @click="openCurriculum()">here</span> - to begin an Extension. You will find related images, model sentences, thought-provoking questions, and many ways to interact and express yourself. Let the power of an image guide your curiousity.
                </div>
                <br>
                <div id='secondSentence'>Designed as an complement to Elementary and Middle School curricula, CIRCLE Extensions for Language Development is powerful for any student who would benefit from exploring English in context, especially English Learners.
                </div>
            </div>
            <span id='pic01' @click="goToUnit('worldCulture', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607374530701" alt=""></span>
            <span id='pic02' @click="goToUnit('geography', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607355264157" alt=""></span>
            <span id='pic03' @click="goToUnit('transportation', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607368906998" alt=""></span>
            <span id='pic04' @click="goToUnit('water', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373472112" alt=""></span>
            <span id='pic05' @click="goToUnit('body', 2)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1605900455005" alt=""></span>
            <span id='pic06' @click="goToUnit('house', 2)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607357615625" alt=""></span>
            <span id='pic07' @click="goToUnit('house', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607356466009" alt=""></span>
            <span id='pic08' @click="goToUnit('color', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607094776189" alt=""></span>
            <span id='pic09' @click="goToUnit('body', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1606771994328" alt=""></span>
            
            <span id='pic10' @click="goToUnit('plant', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607365814604" alt=""></span>
            <span id='pic11' @click="goToUnit('plant', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607366545742" alt=""></span>
            <span id='pic12' @click="goToUnit('house', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607357482372" alt=""></span>
            <span id='pic13' @click="goToUnit('worldCulture', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373921147" alt=""></span>
            <span id='pic14' @click="goToUnit('fall', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607273812513" alt=""></span>
            <span id='pic15' @click="goToUnit('fall', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607274246814" alt=""></span>
            <span id='pic16' @click="goToUnit('color', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607273414308" alt=""></span>
            <span id='pic17' @click="goToUnit('body', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1606773191058" alt=""></span>
            
            <span id='pic18' @click="goToUnit('water', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607355525411" alt=""></span>
            <span id='pic19' @click="goToUnit('worldCulture', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607375331157" alt=""></span>
            <span id='pic20' @click="goToUnit('plant', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607366920136" alt=""></span>
            <span id='pic21' @click="goToUnit('water', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373508510" alt=""></span>
            <span id='pic22' @click="goToUnit('fall', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607274521869" alt=""></span>
            <span id='pic23' @click="goToUnit('house', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607358286735" alt=""></span>
            <span id='pic24' @click="goToUnit('worldCulture', 2)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607374262772" alt=""></span>
            <span id='pic25' @click="goToUnit('worldCulture', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607374033334" alt=""></span>
            <span id='pic26' @click="goToUnit('color', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607094891107" alt=""></span>
            <span id='pic27' @click="goToUnit('water', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373740099" alt=""></span>
            <span id='pic28' @click="goToUnit('space', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607367673949" alt=""></span>
            <span id='pic29' @click="goToUnit('color', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607273145309" alt=""></span>
            <span id='pic30' @click="goToUnit('transportation', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607371499772" alt=""></span>
            <span id='pic31' @click="goToUnit('space', 2)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607367597398" alt=""></span>
            <span id='pic32' @click="goToUnit('worldCulture', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607374883268" alt=""></span>
            <span id='pic33' @click="goToUnit('body', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1606772503460" alt=""></span>
            <span id='pic34' @click="goToUnit('space', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607368042590" alt=""></span>
            <span id='pic35' @click="goToUnit('body', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1606773315833" alt=""></span>
            <span id='pic36' @click="goToUnit('water', 2)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373779141" alt=""></span>
            <span id='pic37' @click="goToUnit('worldCulture', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607374100757" alt=""></span>
            <span id='pic38' @click="goToUnit('fall', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607273917790" alt=""></span>
            <span id='pic39' @click="goToUnit('color', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.amazonaws.com/1607094611400" alt=""></span>
            <span id='pic40' @click="goToUnit('water', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607373555109" alt=""></span>
            <span id='pic41' @click="goToUnit('water', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607372839160" alt=""></span>
            <span id='pic42' @click="goToUnit('geography', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607355203922" alt=""></span>
            <span id='pic43' @click="goToUnit('fall', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607274719496" alt=""></span>
            <span id='pic44' @click="goToUnit('house', 2)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607358059743" alt=""></span>
            <span id='pic45' @click="goToUnit('body', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1606772570934" alt=""></span>
            
            <span id='pic46' @click="goToUnit('transportation', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607369371456" alt=""></span>
            <span id='pic47' @click="goToUnit('plant', 2)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607365690769" alt=""></span>
            <span id='pic48' @click="goToUnit('space', 3)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607367762877" alt=""></span>
            <span id='pic49' @click="goToUnit('house', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607357340545" alt=""></span>
            <span id='pic50' @click="goToUnit('geography', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1607355357715" alt=""></span>

            <span id='pic51' @click="goToUnit('body', 1)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1606772984915" alt=""></span>
            <span id='pic52' @click="goToUnit('body', 4)" class='pictureDisplay'><img src="https://circle-eld.s3.us-east-2.amazonaws.com/1605900249986" alt=""></span>
        </div>

    </div>
</template>

<script>
export default {

    methods: {
        goToUnit(theme, unit) {
            window.open('workSelector?theme=' + theme + '&unit=' + unit, '_self',false);
        },  
        addText(concept) {
            let displayBars = [
                document.getElementById("designOptionsBar"),
                document.getElementById("curriculumOptionsBar"),
                document.getElementById("aboutSandyOptionsBar"),
                document.getElementById("contactOptionsBar"),
            ];
            for (let i = 0; i < displayBars.length; i++) {
                displayBars[i].style.display = "none";
                displayBars[i].style.visibility = "hidden";
            };
            let thisBar = "" + concept + "OptionsBar";
            let displayBar = document.getElementById(thisBar);
            displayBar.style.display = "flex";
            displayBar.style.justifyItems = "center";
            displayBar.style.alignItems = "center";
            displayBar.style.visibility = "visible";
        },
        showPage(component) {
            let curriculumWindow = document.getElementById("curriculumContainer");
            let studentWindow = document.getElementById("studentCurriculum");
            let teacherWindow = document.getElementById("teacherCurriculum");
            let parentWindow = document.getElementById("parentCurriculum");
            let designWindow = document.getElementById("designPage");
            let processWindow = document.getElementById("processPage");
            let inspirationWindow = document.getElementById("inspirationPage");     
            let educatorWindow = document.getElementById("softwareDeveloperLinguistEducator");
            let linguistWindow = document.getElementById("softwareDeveloperLinguistEducator");
            let softwareDeveloperWindow = document.getElementById("softwareDeveloperLinguistEducator");
            let contactWindow = document.getElementById("contactPage");

            studentWindow.style.visibility = "hidden";
            teacherWindow.style.visibility = "hidden";
            parentWindow.style.visibility = "hidden";
            designWindow.style.visibility = "hidden";
            processWindow.style.visibility = "hidden";
            inspirationWindow.style.visibility = "hidden";
            educatorWindow.style.visibility = "hidden";
            linguistWindow.style.visibility = "hidden";
            softwareDeveloperWindow.style.visibility = "hidden";
            contactWindow.style.visibility = "hidden";

            curriculumWindow.style.visibility = 'visible';

            if (component == "student") {
                studentWindow.style.visibility = "visible";   
            } else if (component == "teacher") {
                teacherWindow.style.visibility = "visible";   
            } else if (component == "parent") {
                parentWindow.style.visibility = "visible";   
            } else if (component == "design") {
                designWindow.style.visibility = "visible";   
            } else if (component == "process") {
                processWindow.style.visibility = "visible";   
            } else if (component == "inspiration") {
                inspirationWindow.style.visibility = "visible";   
            } else if (component == "softwareDeveloperLinguistEducator") {
                educatorWindow.style.visibility = "visible";   
            } else if (component == "softwareDeveloperLinguistEducator") {
                linguistWindow.style.visibility = "visible";   
            } else if (component == "softwareDeveloperLinguistEducator") {
                softwareDeveloperWindow.style.visibility = "visible";   
            } else if (component = "contact") {
                contactWindow.style.visibility = "visible";
            }
        },
        closePage(component) {
            let curriculumWindow = document.getElementById("curriculumContainer");

            let studentWindow = document.getElementById("studentCurriculum");
            let teacherWindow = document.getElementById("teacherCurriculum");
            let parentWindow = document.getElementById("parentCurriculum");
            let designWindow = document.getElementById("designPage");
            let processWindow = document.getElementById("processPage");
            let inspirationWindow = document.getElementById("inspirationPage");     
            let educatorWindow = document.getElementById("softwareDeveloperLinguistEducator");
            let linguistWindow = document.getElementById("softwareDeveloperLinguistEducator");
            let softwareDeveloperWindow = document.getElementById("softwareDeveloperLinguistEducator");
            let contactWindow = document.getElementById("contactPage");
            
            studentWindow.style.visibility = "hidden";
            teacherWindow.style.visibility = "hidden";
            parentWindow.style.visibility = "hidden";
            designWindow.style.visibility = "hidden";
            processWindow.style.visibility = "hidden";
            inspirationWindow.style.visibility = "hidden";
            educatorWindow.style.visibility = "hidden";
            linguistWindow.style.visibility = "hidden";
            softwareDeveloperWindow.style.visibility = "hidden";
            contactWindow.style.visibility = "hidden";

            curriculumWindow.style.visibility = 'hidden';
        },
        openCurriculum() {
            window.open ('curriculum4','_self',false)
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

#emailName {
    position: absolute;
    top: 200px;
    left: 105px;
    font-size: 1.2rem;
}

#linkedIn{
    position: absolute;
    top: 250px;
    left: 110px;
    font-size: 1.2rem;
}

#gitHub {
    position: absolute;
    top: 300px;
    left: 136px;
    font-size: 1.2rem;
}

#sandyLord {
    position: absolute;
    top: 120px;
    left: 125px;
    font-size: 3rem;
}

#sandyImage1 {
    object-fit: cover;
    position: absolute;
    top: 60px;
    left: 530px;
    width: 220px;
    height: 350px;
}

#inspirationInfoA {
    position: absolute;
    top: 100px;
    left: 25px;
    font-size: 1.4rem;
    width: 800px;
}

#inspirationInfoB {
    position: absolute;
    top: 270px;
    left: 25px;
    font-size: 1.4rem;
    width: 800px;
}

#sandyJobInterest {
    position: absolute;
    top: 400px;
    left: 25px;
    font-size: 1.4rem;
    width: 800px;
}

#coursesTaken {
    position: absolute;
    top: 330px;
    left: 25px;
    font-size: 1.5rem;
    width: 800px;
    height: 65px;
    border-bottom: 2px solid salmon;
    border-radius: 0;   
}

#contactInfo1 {
    grid-column: 2 / 6;
    text-align: center;
    font-size: 4rem;
    padding: 12px;
    margin: 5px;
    height: 95px;
    width: 350px;
    border-bottom: 2px solid salmon;   
    transform: translateX(-15px) translateY(0px);
}

#softwareDeveloperLinguistEducatorInfo1 {
    grid-column: 2 / 6;
    text-align: center;
    font-size: 2rem;
    padding: 12px;
    margin: 5px;
    height: 95px;
    width: 650px;
    border-bottom: 2px solid salmon;   
    transform: translateX(10px) translateY(0px);
}


#educatorInfo1 {
    position: absolute;
    top: 110px;
    left: 25px;
    font-size: 1.2rem;
    width: 800px;
}

#designInfoA {
    position: absolute;
    top: 100px;
    left: 25px;
    font-size: 1.3rem;
}

#designInfoB {
    position: absolute;
    top: 170px;
    left: 25px;
    font-size: 1.3rem;
}

#designInfoC {
    position: absolute;
    top: 290px;
    left: 25px;
    font-size: 1.3rem;
}

#clickAndPractice {
    position: absolute;
    top: 80px;
    left: 20px;
    width: 200px;
    height: 300px;
    font-size: 1.48em;
    border: 8px solid salmon;
    border-radius: 10px;
}

#selectionForStudent {
    position: absolute;
    top: 60px;
    left: 225px;
    width: 600px;
    cursor: pointer;
}

.closer {
    position: absolute;
    left: 832px;
    top: 7px;
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

#inspirationInfo1 {
    grid-column: 2 / 6;
    text-align: center;
    font-size: 4rem;
    padding: 2px;
    margin: 5px;
    height: 70px;
    border-bottom: 2px solid salmon;   
    transform: translateX(200px) translateY(0px);
}

#processInfo1 {
    grid-column: 2 / 6;
    text-align: center;
    font-size: 4rem;
    padding: 2px;
    margin: 5px;
    height: 70px;
    border-bottom: 2px solid salmon;   
    transform: translateX(-140px) translateY(0px);
}

#designInfo1 {
    grid-column: 3 / 6;
    text-align: center;
    font-size: 4rem;
    padding: 2px;
    margin: 5px;
    height: 70px;
    border-bottom: 2px solid salmon;   
    transform: translateX(150px) translateY(0px);
}

#parentCurriculumInfo1 {
    grid-column: 2 / 6;
    text-align: center;
    font-size: 4rem;
    padding: 2px;
    margin: 5px;
    height: 70px;
    border-bottom: 2px solid salmon;   
    transform: translateX(-140px) translateY(0px);
}

#teacherCurriculumInfo1 {
    grid-column: 2 / 6;
    text-align: center;
    font-size: 2rem;
    padding: 2px;
    height: 50px;
    border-bottom: 2px solid salmon;   
    transform: translateX(0px) translateY(0px);
}

#studentCurriculumInfo1 {
    grid-column: 2 / 6;
    text-align: center;
    font-size: 2.7rem;
    padding: 2px;
    margin: 5px;
    height: 70px;
    border-bottom: 2px solid salmon;   
    transform: translateX(-140px) translateY(0px);
}

#curriculumContainer {
    visibility: hidden;
}

#curriculumContainer > div {
    position: absolute;
    top: 0%;
    left: 0%;
    display: grid;
    grid-template-columns: repeat(11, 1fr);
    grid-auto-rows: repeat(6, 1fr);
    visibility: hidden;
}

.arrows {
    width: 180px;
}

@keyframes blinkFirstArrow {
    0% {opacity: 0.3; transform: scale(1) translateY(-40px) rotate(50deg) translateX(-20px);}
    5% {opacity: 1; transform: scale(1.2) translateY(-40px) rotate(50deg) translateX(-20px);}
    10% {opacity: 0.3; transform: scale(1) translateY(-40px) rotate(50deg) translateX(-20px);}
    20% {opacity: 0.3; transform: scale(1) translateY(-40px) rotate(50deg) translateX(-20px);}
    25% {opacity: 1; transform: scale(1.2) translateY(-40px) rotate(50deg) translateX(-20px);}
    30% {opacity: 0.3; transform: scale(1) translateY(-40px) rotate(50deg) translateX(-20px);}
    100% {opacity: 0.3; transform: scale(1) translateY(-40px) rotate(50deg) translateX(-20px);}
}

@keyframes blinkSecondArrow {
    0% {opacity: 0.3; transform: scale(1) translateY(-270px) rotate(215deg) translateX(-170px);}
    10% {opacity: 0.3; transform: scale(1) translateY(-270px) rotate(215deg) translateX(-170px);}
    15% {opacity: 1; transform: scale(1.2) translateY(-270px) rotate(215deg) translateX(-170px);}
    20% {opacity: 0.3; transform: scale(1) translateY(-270px) rotate(215deg) translateX(-170px);} 
    30% {opacity: 0.3; transform: scale(1) translateY(-270px) rotate(215deg) translateX(-170px);}
    35% {opacity: 1; transform: scale(1.2) translateY(-270px) rotate(215deg) translateX(-170px);}
    40% {opacity: 0.3; transform: scale(1) translateY(-270px) rotate(215deg) translateX(-170px);}
    100% {opacity: 0.3; transform: scale(1) translateY(-270px) rotate(215deg) translateX(-170px);}
}

@keyframes blinkThirdArrow {
    0% {opacity: 0.3; transform: translateX(260px) translateY(-90px) rotate(90deg) scale(1.2);}
    40% {opacity: 0.3; transform: translateX(260px) translateY(-90px) rotate(90deg) scale(1.2);} 
    45% {opacity: 1; transform: translateX(260px) translateY(-90px) rotate(90deg) scale(1.4);}
    94.7% {opacity: 1; transform: translateX(260px) translateY(-90px) rotate(90deg) scale(1.4);}
    100% {opacity: 0.3; transform: translateX(260px) translateY(-90px) rotate(90deg) scale(1.2);}
}

@keyframes colorSee {
    0% { color: black;text-decoration: none;}
    45% { color: black;text-decoration: none;}
    52% {color: purple;text-decoration: underline;}
    94.8% {color: purple;text-decoration: underline;}
    100% {color: black;text-decoration: none;}
}

@keyframes colorListen {
    0% { color: black;text-decoration: none;}
    48% { color: black;text-decoration: none;}
    55% {color: blue;text-decoration: underline;}
    94.9% {color: blue;text-decoration: underline;}
    100% {color: black;text-decoration: none;}
}

@keyframes colorKnow {
    0% { color: black;text-decoration: none;}
    51% { color: black;text-decoration: none;}
    58% {color: gray;text-decoration: underline;}
    95% {color: gray;text-decoration: underline;}
    100% {color: black;text-decoration: none;}
}

@keyframes colorConnect {
    0% { color: black; text-decoration: none;}
    54% { color: black; text-decoration: none;}
    61% {color: yellowgreen; text-decoration: underline;}
    95.1% {color: yellowgreen; text-decoration: underline}
    100% {color: black; text-decoration: none;}
}

@keyframes colorQuestion {
    0% { color: black;text-decoration: none;}
    60% { color: black;text-decoration: none;}
    67% {color: red;text-decoration: underline;}
    95.2% {color: red;text-decoration: underline;}
    100% {color: black;text-decoration: none;}
}

@keyframes colorRemember {
    0% { color: black;text-decoration: none;}
    57% { color: black;text-decoration: none;}
    64% {color: lightblue;text-decoration: underline;}
    95.3% {color: lightblue;text-decoration: underline;}
    100% {color: black;text-decoration: none;}
}

@keyframes enhanceImage {
    0% { opacity: 0.5;}
    67% { opacity: 0.5;}
    75% {opacity: 1;}
    95.4% {opacity: 1;}
    100% {opacity: 0.5;}
}

.share {
    font-family: 'Lato', sans-serif;
    border-radius: 10px;
    font-size: 3em;
    width: 75px;
}

#see {
    grid-column: 2;
    grid-row: 4;
    animation: colorSee 10000ms infinite;
    transform: translateX(150px) translateY(-150px);
}

#listen {
    grid-column: 2;
    grid-row: 4;
    animation: colorListen 10000ms infinite;
    transform: translateX(190px) translateY(-90px);
}

#know {
    grid-column: 2;
    grid-row: 4;
    animation: colorKnow 10000ms infinite;
    transform: translateX(230px) translateY(-30px);
}

#connect {
    grid-column: 2;
    grid-row: 4;
    animation: colorConnect 10000ms infinite;
    transform: translateX(270px) translateY(30px);
}

#remember {
    grid-column: 2;
    grid-row: 4;
    animation: colorRemember 10000ms infinite;
    transform: translateX(310px) translateY(90px);
}

#question {
    grid-column: 2;
    grid-row: 4;
    animation: colorQuestion 10000ms infinite;
    transform: translateX(350px) translateY(150px);
}

#arrow1 {
    grid-column: 1;
    grid-row: 6;
    animation: blinkFirstArrow 10000ms infinite;
}

#arrow2 {
    grid-column: 1;
    grid-row: 6;
    animation: blinkSecondArrow 10000ms infinite;
}

#arrow3 {
    grid-column: 1;
    grid-row: 6;
    animation: blinkThirdArrow 10000ms infinite;
}

#studentsImg {
    grid-column: 1;
    grid-row: 6;
    height: 150px;
    transform: translateY(-70px) translateX(120px);
}

#teacherImg {
    grid-column: 1;
    grid-row: 6;
    height: 150px;
    width: 150px;
    object-fit: cover;
    transform: translateX(20px) translateY(-270px);
}

.explain {
    object-fit: cover;
    width: 75px;
    height: 75px;
    animation: enhanceImage 10000ms infinite;
}

#explainImg1 {
    grid-column: 6;
    grid-row: 1;
}

#explainImg2 {
    grid-column: 7;
    grid-row: 2;
}

#explainImg3 {
    grid-column: 8;
    grid-row: 3;
}

#explainImg4 {
    grid-column: 9;
    grid-row: 4;
}

#explainImg5 {
    grid-column: 8;
    grid-row: 1;
}

#explainImg6 {
    grid-column: 10;
    grid-row: 1;
}

#explainImg7 {
    grid-column: 9;
    grid-row: 2;
}

#explainImg8 {
    grid-column: 11;
    grid-row: 2;
}

#explainImg9 {
    grid-column: 10;
    grid-row: 3;
}

#explainImg10 {
    grid-column: 11;
    grid-row: 4;
}

#explainImg11 {
    grid-column: 10;
    grid-row: 5;
}

#explainImg12 {
    grid-column: 11;
    grid-row: 6;
}

#studentCurriculumInfo2 {
    padding: 2px;
    margin: 5px;
    border: 2px solid salmon;
    background-color: lightcyan;
}

#studentCurriculumInfo3 {
    padding: 2px;
    margin: 5px;
    border: 2px solid salmon;
    background-color: lightcyan;
}

#studentCurriculum {
    visibility: visible;
}

#parentCurriculum {
    visibility: hidden;
}

#teacherCurriculum {
    visibility: hidden;
}

#curriculumContainer {
    position: absolute;
    top: 200px;
    left: 5%;
    background-color: lavender;
    height: 500px;
    width: 900px;
    z-index: 1000000;
    border: 10px solid salmon;
    outline: 3px solid black;
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

#mainDisplay {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    justify-items: center;
    align-items: center;
}

#centerDisplay {
    background-color: lavender;
    grid-column: 3 / 8;
    grid-row: 3 / 8;
}

#centerDisplay {
    font-size: 1.8em;
    padding: 5px;
    margin: 10px;
    border-radius: 30px;
    border: 8px solid salmon;
}

#firstSentence, #secondSentence {
    padding-left: 10px;
}

#firstSentence::first-letter, #secondSentence::first-letter {
    font-size: 80px;
    display: block;
    float: left;
    line-height: 0.5;
    margin: 15px 15px 10px 0;
}

#secondSentence {
    font-size: 1.5rem;
}

img {
    border-radius: 10px;
}

span {
    border-radius: 10px;
}

#pic01 {
    grid-column: 1 / 2;
    grid-row: 1 / 2;
}

#pic02 {
    grid-column: 2 / 3;
    grid-row: 1 / 2;
}

#pic03 {
    grid-column: 3 / 4;
    grid-row: 1 / 2;
}

#pic04 {
    grid-column: 4 / 5;
    grid-row: 1 / 2;
}

#pic05 {
    grid-column: 5 / 6;
    grid-row: 1 / 2;
}

#pic06 {
    grid-column: 6 / 7;
    grid-row: 1 / 2;
}

#pic07 {
    grid-column: 7 / 8;
    grid-row: 1 / 2;
}

#pic08 {
    grid-column: 8 / 9;
    grid-row: 1 / 2;
}

#pic09 {
    grid-column: 9 / 10;
    grid-row: 1 / 2;
}

#pic10 {
    grid-column: 1 / 2;
    grid-row: 2 / 3;
}

#pic11 {
    grid-column: 2 / 3;
    grid-row: 2 / 3;
}

#pic12 {
    grid-column: 3 / 4;
    grid-row: 2 / 3;
} 

#pic13 {
    grid-column: 4 / 5;
    grid-row: 2 / 3;
    border-bottom-right-radius: 100%;
}

#pic13 > img {
    border-bottom-right-radius: 100%;
}

#pic14 {
    grid-column: 6 / 7;
    grid-row: 2 / 3;
    border-bottom-left-radius: 100%;
}

#pic14 > img {
    border-bottom-left-radius: 100%;
}


#pic15 {
    grid-column: 7 / 8;
    grid-row: 2 / 3;
} 

#pic16 {
    grid-column: 8 / 9;
    grid-row: 2 / 3;
}

#pic17 {
    grid-column: 9 / 10;
    grid-row: 2 / 3;
}

#pic18 {
    grid-column: 1 / 2;
    grid-row: 3 / 4;

}

#pic19 {
    grid-column: 2 / 3;
    grid-row: 3 / 4;

} 

#pic20 {
    grid-column: 8 / 9;
    grid-row: 3 / 4;
}

#pic21 {
    grid-column: 9 / 10;
    grid-row: 3 / 4;
}

#pic22 {
    grid-column: 1 / 2;
    grid-row: 4 / 5;

}

#pic23 {
    grid-column: 2 / 3;
    grid-row: 4 / 5;

border-bottom-right-radius: 100%;
}

#pic23 > img {
    border-bottom-right-radius: 100%;
}

#pic24 {
    grid-column: 8 / 9;
    grid-row: 4 / 5;
    border-bottom-left-radius: 100%;
}

#pic24 > img {
    border-bottom-left-radius: 100%;
}

#pic25 {
    grid-column: 9 / 10;
    grid-row: 4 / 5;
}

#pic26 {
    grid-column: 1 / 2;
    grid-row: 5 / 6;
}

#pic27 {
    grid-column: 9 / 10;
    grid-row: 5 / 6;
}

#pic28 {
    grid-column: 1 / 2;
    grid-row: 6 / 7;
}

#pic29 {
    grid-column: 2 / 3;
    grid-row: 6 / 7;
    border-top-right-radius: 100%;
}

#pic29 > img {
    border-top-right-radius: 100%;
} 

#pic30 {
    grid-column: 8 / 9;
    grid-row: 6 / 7;
    border-top-left-radius: 100%;
}

#pic30 > img {
    border-top-left-radius: 100%;
}

#pic31 {
    grid-column: 9 / 10;
    grid-row: 6 / 7;
}

#pic32 {
    grid-column: 1 / 2;
    grid-row: 7 / 8;
}

#pic33 {
    grid-column: 2 / 3;
    grid-row: 7 / 8;
} 

#pic34 {
    grid-column: 8 / 9;
    grid-row: 7 / 8;
}

#pic35 {
    grid-column: 9 / 10;
    grid-row: 7 / 8;
}

#pic36 {
    grid-column: 1 / 2;
    grid-row: 8 / 9;
}

#pic37 {
    grid-column: 2 / 3;
    grid-row: 8 / 9;
}

#pic38 {
    grid-column: 3 / 4;
    grid-row: 8 / 9;
} 

#pic39 {
    grid-column: 4 / 5;
    grid-row: 8 / 9;
    border-top-right-radius: 100%;
}

#pic39 > img {
    border-top-right-radius: 100%;
}

#pic40 {
    grid-column: 6 / 7;
    grid-row: 8 / 9;
    border-top-left-radius: 100%;
}

#pic40 > img {
    border-top-left-radius: 100%;
}

#pic41 {
    grid-column: 7 / 8;
    grid-row: 8 / 9;
} 

#pic42 {
    grid-column: 8 / 9;
    grid-row: 8 / 9;
}

#pic43 {
    grid-column: 9 / 10;
    grid-row: 8 / 9;
}

#pic44 {
    grid-column: 1 / 2;
    grid-row: 9 / 10;
}

#pic45 {
    grid-column: 2 / 3;
    grid-row: 9 / 10;
}

#pic46 {
    grid-column: 3 / 4;
    grid-row: 9 / 10;
}

#pic47 {
    grid-column: 4 / 5;
    grid-row: 9 / 10;
}

#pic48 {
    grid-column: 5 / 6;
    grid-row: 9 / 10;
}

#pic49 {
    grid-column: 6 / 7;
    grid-row: 9 / 10;
}

#pic50 {
    grid-column: 7 / 8;
    grid-row: 9 / 10;
}

#pic51 {
    grid-column: 8 / 9;
    grid-row: 9 / 10;
}

#pic52 {
    grid-column: 9 / 10;
    grid-row: 9 / 10;
}

span > img {
    opacity: 0.8;
}

#mainDisplay > span > img:hover{
    opacity: 1;
    transform: scale(2);
    border: 3px solid lightsalmon;
    cursor: pointer;
    z-index: 50;
}

#mainDisplay > span:hover{
    z-index: 49;
}

.pictureDisplay {
    background-color: white;
    margin: 5px;
}

.pictureDisplay > img {
    object-fit: cover;
    height: 70px;
    width: 100px;
}


#optionsBar {
    display: flex;
    background-color: rgb(75, 221, 139);
    height: 65px;
}

#optionsBar > div {
    display: flex;
}

#optionsBar > div > span {
    font-size: 1.2rem;
    background-color: rgb(250, 195, 189);
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}

#optionsBar > div > span:hover {
    color:white;
    cursor: pointer;
    background-color: rgb(211, 107, 96);
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
    font-size: 2rem;
    margin: auto;
    background: salmon;
    color: black;
    padding: 9px;
    border-radius: 5px;
}

#navbar > span:hover {
    color:white;
    cursor: pointer;
    background-color: rgb(211, 107, 96);
}

#logoFinal {
    border-color: salmon;
}

</style>