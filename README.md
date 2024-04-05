<!DOCTYPE html>
<html lang="en">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            text-decoration: none;
            border: none;
            outline: none;
            scroll-behavior: smooth;
            font-family: "Reddit Mono", monospace;
            font-optical-sizing: auto;
        }

        h1 {
            padding: 20px;
            display: flex;
            justify-content: center;
            font-size: min(40px, 10vw);
        }

        h2 {
            font-size: min(30px, 10vw);
            padding: 20px;
            display: flex;
            justify-content: center;
        }

        p {
            font-size: min(20px, 5vw);
            font-weight: 100;
            justify-content: center;
            display: flex;
            margin: min(30px, 5vw);
        }
        
        body {
            min-width: 100vw;
            min-height: 100vh;
            transition: background-color 0.5s ease;
            overflow-x: hidden;
        }

        @keyframes move {
            0% {
              background-position: 0 0;
            }
            100% {
              background-position: 40px 40px;
            }
        }
          
        
        @keyframes flyIn {
            from {
                opacity: 0;
                transform: translateX(-100%);
            }
            to {
                opacity: 1;
                transform: translateX(0);
                visibility: visible; 
            }
        }
        
        @keyframes text-animation {
            0% {margin-top: 0;}
            10% {margin-top: 0;}
            20% {margin-top: -5.62rem;}
            30% {margin-top: -5.62rem;}
            40% {margin-top: -11.24rem;}
            60% {margin-top: -11.24rem;}
            70% {margin-top: -5.62rem;}
            80% {margin-top: -5.62rem;}
            90% {margin-top: 0;}
            100% {margin-top: 0;}
        }
        
        @keyframes slide-in-top {
            0% {
              transform: translateY(-50px);
              opacity: 0;
            }
          
            100% {
              transform: translateY(0);
              opacity: 1;
            }
        }
        
        @keyframes slide-hover {
            0% { width: 0%; }
            70% { width: calc(var(--percentage) / 0.95); }
            100% { width: calc(var(--percentage)); }
        }
        
        
        @keyframes slide {
            0% { width: calc(var(--percentage) / 1); }
            50% { width: calc(var(--percentage) / 1.08); }
            70% { width: calc(var(--percentage) / 0.98); }
            85% { width: calc(var(--percentage) / 1.08); }
            100% { width: calc(var(--percentage) / 1); }
        }
        
        @keyframes flip5 {
            0% { margin-top: -450px; }
            5% { margin-top: -360px; }
            20% { margin-top: -360px; }
            25% { margin-top: -270px; }
            40% { margin-top: -270px; }
            45% { margin-top: -180px; }
            60% { margin-top: -180px; }
            65% { margin-top: -90px; }
            80% { margin-top: -90px; }
            85% { margin-top: 0px; }
            99.99% { margin-top: 0px; }
            100% { margin-top: -450px; }
        }

        .flip5 { animation: flip5 12s cubic-bezier(0.23, 1, 0.32, 1.2) infinite; }

        .blur {
            backdrop-filter: blur(5px);
            background-color: rgba(0, 0, 0, 0.2);
        }

        .body {
            color: white;
            padding: 10px 20px 10px 20px;
        }
        
        .body-light {
            color: black;
            padding: 10px 20px 10px 20px;
        }

        .body-light p {
            font-weight: 500;
        }

        .body-light .wordCarousel{
            color: black;
            font-weight: 500;
        }

        .body-light .wordCarousel li {
            color: black;
            font-weight: 700;
        }
        
        .Background {
            width: 100%;
            height: 100%;
            background: #121212;
            background: linear-gradient(
              135deg,
              #121212 25%,
              #1a1a1a 25%,
              #1a1a1a 50%,
              #121212 50%,
              #121212 75%,
              #1a1a1a 75%,
              #1a1a1a
            );
            background-size: 40px 40px;
            animation: move 4s linear infinite;
        }
        
        .Background-light {
            width: 100%;
            height: 100%;
            background: #969696;
            background: linear-gradient(
              135deg,
              #969696 25%,
              #c2c2c2 25%,
              #c2c2c2 50%,
              #969696 50%,
              #969696 75%,
              #c2c2c2 75%,
              #c2c2c2
            );
            background-size: 40px 40px;
            animation: move 4s linear infinite;
        }
        
        .wordCarousel {
            justify-content: center;
            flex-wrap: wrap;
            margin: 10px 0 0 0;
            font-size: min(30px, 5vw);
            font-weight: 100;
            font-weight: 100;
            color: #eee;
            display: flex;
            div {
                overflow: hidden;
                position: relative;
                float: right;
                height: 65px;
                padding: 10px;
                padding-top: 10px;
                margin-top: -10px;
                li {
                    color: #eee;
                    font-weight: 700;
                    padding: 0 10px;
                    height: 45px;
                    margin-bottom: 45px;
                    display: block;
                    position:relative;
                }
            }
        }
        
        .flip5 { animation: flip5 12s cubic-bezier(0.23, 1, 0.32, 1.2) infinite; }
        
        .social-card {
            position: fixed;
            bottom: 20px;
            right: 20px;
            padding: 20px;
            width: fit-content;
            height: fit-content;
            backdrop-filter: blur(5px);
            background-color: rgba(0, 0, 0, 0.2);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
        }
          
        .socialContainer {
            width: min(80px, 10vw);
            height: min(64px, 7vw);
            backdrop-filter: blur(5px);
            background-color: rgba(0, 0, 0, 0.4);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            transition-duration: .3s;
        }
        
        .containerOne:hover {
            background-color: rgb(214, 41, 118, 0.2);
            transition-duration: .3s;
        }
        
        .containerTwo:hover {
            background-color: rgb(0, 172, 238, 0.2);
            transition-duration: .3s;
        }
        
        .containerThree:hover {
            background-color: rgb(0, 114, 177, 0.2);
            transition-duration: .3s;
        }
        
        .containerFour:hover {
            background-color: rgb(18, 140, 126, 0.2);
            transition-duration: .3s;
        }
          
        .socialContainer:active {
            transform: scale(0.9);
            transition-duration: .3s;
        }
          
        .socialSvg {
            width: 25px;
        }
          
        .socialSvg path {
            fill: rgb(255, 255, 255);
        }
          
        .socialContainer:hover .socialSvg {
            animation: slide-in-top 0.3s both;
        }
        
        
        .themeContainer {
            display: flex;
            flex-direction: row-reverse;
        }
        
        .theme-switch {
            z-index: 1000;
            position: fixed;
            display: flex;
            justify-content: center;
            direction: rtl;
            margin: 10px;
            width: min(300px, 23vw);
            height: auto;
        }
        
        .welcome-container-1 {
            display: flex;
            align-content: center;
            flex-direction: column;
        }
        
        .card {
            margin: 50px 0 0 0;
            align-self: center;
            align-items: center;
            width: 500px;
            backdrop-filter: blur(5px);
            background-color: rgba(0, 0, 0, 0.2);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
            overflow: hidden;
            transition: all 1s;
        }
        
        .card:hover {
            width: 520px;
            backdrop-filter: blur(10px);
            background-color: rgba(0, 0, 0, 0.2);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            transition: all 1s;
        }
        
        .card:hover .skill-percent {
            animation: slide-hover 2s ease-in-out forwards;
            background-color: rgba(1, 167, 14, 0.74);
        }
          
        .header-skills {
            backdrop-filter: blur(10px);
            background-color: rgba(0, 0, 0, 0.2);
            color: #fff;
            padding: 20px;
            text-align: center;
            font-size: min(20px, 10vw);
            font-weight: 100;
        }
          
        .skill {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
          
        .skill-name {
            width: 120px;
            font-size: min(15px, 3vw);
            font-weight: 100;
        }
          
        .skill-level {
            width: 280px;
            height: 10px;
            backdrop-filter: blur(2px);
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            overflow: hidden;
            margin-left: 20px;
        }
          
        .skill-percent {
            backdrop-filter: blur(2px);
            background-color: rgba(0, 0, 0, 0.1);
            animation: slide 8s ease-in-out forwards infinite;
            height: 100%;
        }
          
        .skill-percent-number {
            margin-left: 10px;
            font-size: 16px;
        }

        .body-light .card:hover .skill-percent {
            animation: slide-hover 2s ease-in-out forwards;
            background-color: rgba(0, 97, 8, 0.74);
        } 

        .body-light .skill-level {
            width: 280px;
            height: 10px;
            backdrop-filter: blur(2px);
            background-color: rgba(29, 29, 29, 0.2);
            border-radius: 10px;
            overflow: hidden;
            margin-left: 20px;
        }

        #welcome {
            text-shadow: 0 0 7px rgba(255,255,255,.3), 0 0 3px rgba(255,255,255,.3);
        }
          
        section {
            padding: 0px 40px 0px 40px;
        }

        #theme-checkbox {
            display: none;
          }
          
        #theme-checkbox + label {
            font-size: 2rem;
            height: 1em;
            width: 2.5em;
            border-radius: 0.25em;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            backdrop-filter: blur(5px);
            background-color: rgba(0, 0, 0, 0.2);
            position: relative;
        }
          
        #theme-checkbox:checked + label {
            backdrop-filter: blur(5px);
            background-color: rgba(0, 0, 0, 0.2);
        }
          
        #theme-checkbox + label:active {
            transform: scale(0.85);
            transition: transform 0.2s;
        }
          
        #theme-checkbox + label div {
            width: 0.8em;
            height: 0.8em;
            border-radius: inherit;
            position: absolute;
            top: 0.1em;
            left: 0.1em;
            z-index: 10;
            transition: 0.5s cubic-bezier(1, 0.33, 0.11, 1.34);
            background-color: #f2f2f2;
        }
          
        #theme-checkbox:checked + label div {
            /* left: calc(2.5em - .8em - .1em); */
            left: 1.6em;
            background-color: #212121;
        }
          
        #theme-checkbox + label span {
            display: flex;
        }
          
        #theme-checkbox + label svg {
            display: inline-block;
            height: 1em;
            width: 1em;
            padding: 0.15em;
            box-sizing: border-box;
        }
          
        #theme-checkbox + label span:first-of-type {
            color: #3a3a3a;
        }
          
        #theme-checkbox + label span:last-of-type {
            color: #cecece;
        }   
        
        @media only screen and (max-width: 1000px) {
             
            .socialSvg {
                width: 35px;
            }

            .social-card {
                bottom: 30px;
                right: 30px;
                padding: 30px;
            }

            .socialContainer {
                width: min(200px, 10vw);
                height: min(160px, 7vw);
            }

            .containerOne:hover {
                background-color: rgb(214, 41, 118, 0.2);
            }
            
            .containerTwo:hover {
                background-color: rgb(0, 172, 238, 0.2);
            }
            
            .containerThree:hover {
                background-color: rgb(0, 114, 177, 0.2);
            }
            
            .containerFour:hover {
                background-color: rgb(18, 140, 126, 0.2);
            }

            .card {
                margin: 20px 0 0 0;
                width: 1100px;
                height: 740px;
                border-radius: 10px;
            }
            
            .card:hover {
                width: 1100px;
            }

            .header-skills {
                font-size: min(40px, 10vw);
            }
              
            .skill {
                display: flex;
                flex-direction: column;
                align-items: center;
                margin-bottom: 20px;
            }
              
            .skill-name {
                display: flex;
                justify-content: center;
                width: 300px;
                font-size: min(50px, 3vw);
                font-weight: 100;
            }
              
            .skill-level {
                width: 700px;
                height: 10px;
            }
              
            .skill-percent {
                margin-top: 30px;
            }
              
            .skill-percent-number {
                margin-left: 20px;
                font-size: 30px;
            }

            .card:hover {
                margin: 20px 0 0 0;
                width: 1000px;
                height: 740px;
            }
            
            .card:hover .skill-percent {
                margin-top: 30px;
            }

            .wordCarousel {
                margin: 20px 0 0 0;
                font-size: min(50px, 5vw);
                font-weight: 200;
                font-weight: 200;
            }

            .wordCarousel div li {
                font-weight: 800;
                padding: 0 10px;
                height: 45px;
                margin-bottom: 45px;
                display: block;
                position:relative;
            }

            #theme-checkbox + label {
                font-size: 4rem;
            }
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Reddit+Mono:wght@200..900&display=swap" rel="stylesheet">
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.1/gsap.min.js"></script>
    <script>
        let themeIndicator = 0;
        document.addEventListener('DOMContentLoaded', function() {
            document.querySelectorAll('.theme-switch').forEach(function(Switch) {
                Switch.addEventListener('change', function() {
                    if (themeIndicator % 2 === 0) {
                        document.body.classList.add('Background-light');
                        document.body.classList.remove('Background');
                        document.body.classList.add('body-light');
                        document.body.classList.remove('body');
                    } else {
                        document.body.classList.add('Background');
                        document.body.classList.remove('Background-light');
                        document.body.classList.add('body');
                        document.body.classList.remove('body-light');
                    }
                    themeIndicator++;
                });
            });
        });
    </script>
    <body class="body Background">
        <div class="themeContainer">
          <div class="theme-switch hoverable">
            <input type="checkbox" id="theme-checkbox" />
            <label for="theme-checkbox">
              <div></div>
              <span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  class="w-6 h-6"
                  >
                  <path
                    fill-rule="evenodd"
                    d="M9.528 1.718a.75.75 0 01.162.819A8.97 8.97 0 009 6a9 9 0 009 9 8.97 8.97 0 003.463-.69.75.75 0 01.981.98 10.503 10.503 0 01-9.694 6.46c-5.799 0-10.5-4.701-10.5-10.5 0-4.368 2.667-8.112 6.46-9.694a.75.75 0 01.818.162z"
                    clip-rule="evenodd"
                  ></path>
                </svg>
              </span>
              <span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  class="w-6 h-6"
                  >
                  <path
                    d="M12 2.25a.75.75 0 01.75.75v2.25a.75.75 0 01-1.5 0V3a.75.75 0 01.75-.75zM7.5 12a4.5 4.5 0 119 0 4.5 4.5 0 01-9 0zM18.894 6.166a.75.75 0 00-1.06-1.06l-1.591 1.59a.75.75 0 101.06 1.061l1.591-1.59zM21.75 12a.75.75 0 01-.75.75h-2.25a.75.75 0 010-1.5H21a.75.75 0 01.75.75zM17.834 18.894a.75.75 0 001.06-1.06l-1.59-1.591a.75.75 0 10-1.061 1.06l1.59 1.591zM12 18a.75.75 0 01.75.75V21a.75.75 0 01-1.5 0v-2.25A.75.75 0 0112 18zM7.758 17.303a.75.75 0 00-1.061-1.06l-1.591 1.59a.75.75 0 001.06 1.061l1.591-1.59zM6 12a.75.75 0 01-.75.75H3a.75.75 0 010-1.5h2.25A.75.75 0 016 12zM6.697 7.757a.75.75 0 001.06-1.06l-1.59-1.591a.75.75 0 00-1.061 1.06l1.59 1.591z"
                  ></path>
                </svg>
              </span>
            </label>
          </div>      
        </div>
        <section id="welcome">
          <h4 class="wordCarousel">
            <span>Hey there, Welcome, I'm </span>
            <div>
              <ul class="flip5">
                <li>a Kickboxer</li>
                <li>a Programmer</li>
                <li>a Student</li>
                <li>a Mathematician</li>
                <li>Toby Chen</li>
              </ul>
            </div>
          </h4>
          <div class="col-sm-12 welcome-container-1">
            <div class="card">
              <div class="header-skills">My Skills</div>
              <div class="body">
                <div class="skill">
                  <div class="skill-name">HTML</div>
                  <div class="skill-level">
                    <div class="skill-percent" style="--percentage: 70%"></div>
                  </div>
                <div class="skill-percent-number">70%</div>
                </div>
                <div class="skill">
                  <div class="skill-name">CSS</div>
                  <div class="skill-level">
                    <div class="skill-percent" style="--percentage: 65%"></div>
                  </div>
                  <div class="skill-percent-number">65%</div>
                </div>
                <div class="skill">
                  <div class="skill-name">JavaScript</div>
                  <div class="skill-level">
                    <div class="skill-percent" style="--percentage: 75%"></div>
                  </div>
                  <div class="skill-percent-number">75%</div>
                </div>
                <div class="skill">
                  <div class="skill-name">Python</div>
                  <div class="skill-level">
                    <div class="skill-percent" style="--percentage: 90%"></div>
                  </div>
                  <div class="skill-percent-number">90%</div>
                </div>
                <div class="skill">
                  <div class="skill-name">Java</div>
                  <div class="skill-level">
                    <div class="skill-percent" style="--percentage: 85%"></div>
                  </div>
                  <div class="skill-percent-number">85%</div>
                </div>
                <div class="skill">
                  <div class="skill-name">SQL</div>
                  <div class="skill-level">
                    <div class="skill-percent" style="--percentage: 56%"></div>
                  </div>
                  <div class="skill-percent-number">56%</div>
                </div>
              </div>
            </div>          
          </div>
        </div>
        <div class="col-sm-12">
          <p>Current student at Queen Marys University of London studying Mathematics. Despite my degree, I'm always coding as its a hobby of mine. I hope to build up an extensive portfolio and work within tech one day.</p>
        </div>
        <div class="col-sm-12">
            <h1>Current Projects</h1>
            <h2>🖥️ Website</h2>
            <p>Currently developing my Website to show off my portfolio, which will be responsive and contains all my Mathematical notes</p>
            <h2>🐍 Python Trader</h2>
            <p>I am also coding a python trader which i hope to use to return real profits. Making use of scraping APIs and financial market data.</p>
          </div>
        <div class="col-sm-12">
            <h1>Hobbies</h1>
            <h2>🥊 Kickboxing/ Muay Thai</h2>
            <p>National Kickboxer and recent Muay Thai fighter.</p>
            <h2>🏉 Rugby</h2>
            <p>Playing for QMRFC 1st team</p>
            <h2>🎸 Guitar</h2>
            <p>Long time guitar player.</p>
            <h2>⌨️ Coding</h2>
            <p>Enjoyment through the creation of new things, and learning new skills.</p>
        </div>
        <div class="col-sm-12" style="margin:  200px 0 0 0;">
            <p>Thankyou For Visiting!</p>
        </div>
        </section>
        <div class="social-card">
          <a href="https://www.instagram.com/tobychen1337/" target="_blank" class="socialContainer containerOne">
            <svg class="socialSvg instagramSvg" viewBox="0 0 16 16"> <path d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.917 3.917 0 0 0-1.417.923A3.927 3.927 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.916 3.916 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.926 3.926 0 0 0-.923-1.417A3.911 3.911 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0h.003zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599.28.28.453.546.598.92.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.47 2.47 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.478 2.478 0 0 1-.92-.598 2.48 2.48 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233 0-2.136.008-2.388.046-3.231.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92.28-.28.546-.453.92-.598.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045v.002zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92zm-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217zm0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334z"></path> </svg>
          </a>
          
          <a href="https://github.com/ToadBoyChen"  target="_blank" class="socialContainer containerTwo">
            <svg class="socialSvg githubSvg" viewBox="0 0 24 24"> <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"></path> </svg>              </a>
            
          <a href="https://www.linkedin.com/in/toby-chen-167519298/" target="_blank" class="socialContainer containerThree">
            <svg class="socialSvg linkdinSvg" viewBox="0 0 448 512"><path d="M100.28 448H7.4V148.9h92.88zM53.79 108.1C24.09 108.1 0 83.5 0 53.8a53.79 53.79 0 0 1 107.58 0c0 29.7-24.1 54.3-53.79 54.3zM447.9 448h-92.68V302.4c0-34.7-.7-79.2-48.29-79.2-48.29 0-55.69 37.7-55.69 76.7V448h-92.78V148.9h89.08v40.8h1.3c12.4-23.5 42.69-48.3 87.88-48.3 94 0 111.28 61.9 111.28 142.3V448z"></path></svg>
          </a>
          
          <a href="tel:07714387919"  target="_blank" class="socialContainer containerFour">
            <svg class="socialSvg whatsappSvg" viewBox="0 0 16 16"> <path d="M13.601 2.326A7.854 7.854 0 0 0 7.994 0C3.627 0 .068 3.558.064 7.926c0 1.399.366 2.76 1.057 3.965L0 16l4.204-1.102a7.933 7.933 0 0 0 3.79.965h.004c4.368 0 7.926-3.558 7.93-7.93A7.898 7.898 0 0 0 13.6 2.326zM7.994 14.521a6.573 6.573 0 0 1-3.356-.92l-.24-.144-2.494.654.666-2.433-.156-.251a6.56 6.56 0 0 1-1.007-3.505c0-3.626 2.957-6.584 6.591-6.584a6.56 6.56 0 0 1 4.66 1.931 6.557 6.557 0 0 1 1.928 4.66c-.004 3.639-2.961 6.592-6.592 6.592zm3.615-4.934c-.197-.099-1.17-.578-1.353-.646-.182-.065-.315-.099-.445.099-.133.197-.513.646-.627.775-.114.133-.232.148-.43.05-.197-.1-.836-.308-1.592-.985-.59-.525-.985-1.175-1.103-1.372-.114-.198-.011-.304.088-.403.087-.088.197-.232.296-.346.1-.114.133-.198.198-.33.065-.134.034-.248-.015-.347-.05-.099-.445-1.076-.612-1.47-.16-.389-.323-.335-.445-.34-.114-.007-.247-.007-.38-.007a.729.729 0 0 0-.529.247c-.182.198-.691.677-.691 1.654 0 .977.71 1.916.81 2.049.098.133 1.394 2.132 3.383 2.992.47.205.84.326 1.129.418.475.152.904.129 1.246.08.38-.058 1.171-.48 1.338-.943.164-.464.164-.86.114-.943-.049-.084-.182-.133-.38-.232z"></path> </svg>
          </a>
        </div>
    </body>
    <footer>

    </footer>
</html>
