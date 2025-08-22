<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Reflection & Recording</title>

    <!-- Include lamejs for MP3 encoding -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/lamejs/1.2.0/lame.min.js"></script>

    <!--start of CSS-->
    <style>
      @font-face {
        font-family: "WSWF";
        font-weight: normal;
        font-style: normal;
        src: url(https://static1.squarespace.com/static/67e2ec427693384efd32fd14/t/67e2ef48ad3fd24bbab4c2ae/1742925640408/WWM_Century_Proportional.otf)
          format("opentype");
      }

      :root {
        --heading-font-font-family: "WSWF";
        --body-font-font-family: "WSWF";
        --meta-font-font-family: "WSWF";
        --primary-button-font-font-family: "WSWF";
        --secondary-button-font-font-family: "WSWF";
        --tertiary-button-font-font-family: "WSWF";
        --site-title-font-font-family: "WSWF";
      }

      * {
        font-family: "WSWF", sans-serif !important;
      }

      body {
        background-color: white;
        color: #333;
        height: 700px;
        margin: 0;
        display: flex;
        justify-content: center;
        align-items: center;
      }

      .container {
        background: white;
        border-radius: 12px;
        padding: 30px 40px;
        width: 980px;
        height: 610px;
        box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.35);
        position: relative;
        z-index: 1;
      }

     .tabs {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;
      margin-bottom: 20px;
      }

      .tab {
      padding: 6px;
      border-radius: 9px;
      font-size: 14px;
      cursor: pointer;
     color: grey;
      }

      .tab.active {
      color: black;
      font-weight: bold;
      }

      .middle-tabs {
      display: flex;
      justify-content: space-evenly;
      flex: 1;
      }

      .guided-flow {
        font-size: 16px;
        color: #333;
        line-height: 1.4;
        margin: 0;
        padding: 0;
      }

      .guided-flow p {
        margin: 0;
        padding: 0;
      }

      .flow p {
        margin: 0;
        padding: 0;
        line-height: 1.2;
      }

      .instructions {
        line-height: 1.4;
        margin: 20px 0;
      }

      .step {
        margin-bottom: 8px;
      }

      .step-title {
        font-weight: bold;
        margin-bottom: 4px;
      }

      .step-text {
        margin: 0;
        font-size: 20px;
      }

      .color {
        color: grey;
        font-size: 15px;
      }

      .button-gap {
        display: flex;
        gap: 378px;
        border-radius: 1px;
        padding: 8px 16px;
        white-space: nowrap;
        text-align: center;
        margin-top: 40px;
      }

      .button-down-colour {
        margin-top: 175px;
        color: white;
        padding: 12px 20px;
        background-color: #0a0a0f;
        border-radius: 0px;
        float: left;
        height: 60px;
        width: 140px;
      }

    

      button {
        padding: 10px;
        border: none;
        border-radius: 8px;
        font-size: 14px;
        cursor: pointer;
      }

      .btn-primary {
        background: black;
        color: white;
        border-radius: 2px;
        padding: 12px 20px;
        margin-left: 0;
        margin-top: 50px;
      }

      .begin {
        background: black;
        color: white;
        border-radius: 2px;
        padding: 12px 20px;
        margin-left: 0;
        margin-top: 25px;
        height: 57px;
        width: 83px;
      }

      .agree-btn {
        margin-top: 100px;
        float: left;
      }

      .disagree-btn {
        margin-top: 100px;
        float: right;
        background: #f3f3f3;
        color: black;
      }

      .agree-btn {
        width: 165px;
        height: 55px;
      }

      .disagree-btn {
        width: 240px;
        height: 55px;
      }

      .font {
        font-size: 20px;
        margin-left: 0;
        padding-left: 0;
      }

      input[type="text"] {
        width: 100%;
        padding: 8px 0;
        border: none;
        border-bottom: 2px solid #333;
        background: transparent;
        font-size: 18px;
        outline: none;
        margin: 10px 0;
        transition: border-color 0.3s;
      }

      input[type="text"]:focus {
        border-bottom: 2px solid black;
      }

      .start-again-btn {
      background: black;
      color: white;
      border: none;
      border-radius: 2px;
      padding: 8px 14px;
      font-size: 14px;
      cursor: pointer;
      position: absolute;  
      top: 20px;          
      right: 20px;       
    z-index: 10;  
      width: 165px;
      height: 55px;      
}



      .screen {
        width: 50%;
        height: 1px;
        margin: 10px auto;
      }

      #timer-display {
        position: absolute;
        right: 40px;
        bottom: 179px;
        font-weight: bold;
        font-size: 14px;
      }

      .progress-bar {
        position: absolute;
        bottom: 50px;
        left: 9px;
        right: 40px;
        height: 8px;
        background: #eee;
        border-radius: 5px;
        overflow: hidden;
        bottom: 165px;
      }

      .progress {
        height: 100%;
        background: black;
        width: 0%;
        transition: width 0.3s;
      }

      .skip-btn {
        position: absolute;
        bottom: 90px;
        right: 40px;
        background: #f3f3f3;
        padding: 10px 16px;
        border-radius: 1px;
        cursor: pointer;
        height: 57px;
        width: 83px;
      }

      .start-record {
        background: black;
        color: white;
        padding: 12px;
        font-size: 1rem;
        border-radius: 2px;
        width: 165px;
        height: 55px;
        margin-top: 40px;
      }

      .stop-record {
        background: black;
        color: white;
        padding: 12px;
        font-size: 1rem;
        border-radius: 2px;
        height: 55px;
        width: 165px;
        margin-top: 40px;
      }

      .background {
        height: 500px;
        background-image: url("");
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
      }
  
      .status {
        font-size: 0.9rem;
        color: #777;
        margin-bottom: 8px;
      }

      .size {
        font-size: 35px;
        margin-left: 0;
        padding-left: 0;
        text-align: left;
      }

      .thankyou {
        font-size: 35px;
        text-align: left;
      }

      #screen-welcome {
        padding-left: 0;
        margin-left: 0;
      }

      #screen-welcome .guided-flow,
      #screen-welcome .instructions {
        padding-left: 0;
        margin-left: 0;
      }

      #screen-waiver {
        padding-left: 0;
        margin-left: 0;
      }

      #screen-welcome .guided-flow,
      #screen-waiver .guided-flow,
      #screen-reflection .guided-flow,
      #screen-recording .guided-flow,
      #screen-thankyou .guided-flow {
        margin-top: 60px;
      }

      #screen-waiver .name {
        margin-top: 40px;
        display: block;
      }

      #screen-waiver input[type="text"] {
        margin-top: 10px;
      }

      #screen-reflection {
        padding-left: 0;
        margin-left: 0;
        text-align: center;
        position: relative;
        height: 100%;
      }

      #screen-recording {
        padding-left: 0;
        margin-left: 0;
      }

      #screen-thankyou {
        padding-left: 0;
        margin-left: 0;
        text-align: center;
      }

      #record-status {
        display: none;
      }

      .progress-bar-recording {
        width: 100%;
        height: 8px;
        background: #eee;
        border-radius: 5px;
        margin-top: 220px;
        overflow: hidden;
      }

      #record-progress {
        height: 100%;
        width: 0%;
        background: black;
        transition: width 0.3s;
      }

      #record-timer {
        position: absolute;
        right: 40px;
        bottom: 190px;
        font-weight: bold;
        font-size: 14px;
      }
    </style>
  </head>
  <!--start of HTML-->
  <body>

    <button class="start-again-btn" onclick="showScreen('welcome')">
    Start again
  </button>

    <div class="container">
      <!--nav bar-->
      <div class="tabs">
  <div class="tab active" id="tab-welcome">Welcome</div>
  
  <div class="middle-tabs">
    <div class="tab" id="tab-waiver">Waiver</div>
    <div class="tab" id="tab-reflection">Reflection</div>
    <div class="tab" id="tab-recording">Recording</div>
  </div>
  
  <div class="tab" id="tab-thankyou">Thank you</div>
</div>
      <!-- NEW BUTTON -->
  
      <!-- Welcome -->
      <div id="screen-welcome">
        <div class="guided-flow">
          <p class="font">This guided flow invites you to pause,</p>
          <p class="font">reflect, and optionally record a short message.</p>
          <p class="font">You can proceed without recording if you prefer.</p>
        </div>

        <div class="instructions">
          <div class="step">
            <div class="step-title"><span class="color">Step 1:</span></div>
            <p class="step-text">
              Read and sign the consent waiver or continue
            </p>
            <div class="flow"><p class="font">without recording.</p></div>
          </div>

          <div class="step">
            <div class="step-title"><span class="color">Step 2:</span></div>
            <p class="step-text">Take a brief reflection pause.</p>
          </div>

          <div class="step">
            <div class="step-title"><span class="color">Step 3:</span></div>
            <p class="step-text">If you consented, record up to 3 minutes.</p>
          </div>
        </div>

        <button class="begin" onclick="showScreen('waiver')">Begin</button>
      </div>

      <!-- Waiver -->
      <div id="screen-waiver" style="display: none">
        <div class="guided-flow">
          <p class="font">We would like to record your thoughts.</p>
          <p class="font">If you agree, Please sign below to consent</p>
          <p class="font">to recording and storage for this experience.</p>
        </div>
        <br>
        <p class="name">Your name <span class="color">(for consent)</span></p>
       
        <input type="text" id="consentName" placeholder="Type your name" autocomplete="off">

        <button class="btn-primary agree-btn" onclick="submitConsent()">
          I agree and sign
        </button>
        <button
          class="btn-primary disagree-btn"
          onclick="goToReflection(false)"
        >
          I don't agree – reflect only
        </button>
      </div>

      <!-- Reflection -->
      <div id="screen-reflection" style="display: none">
        <div class="guided-flow">
          <p class="size">Take a moment to breathe</p>
          <p class="size">and gather your thoughts.</p>
          <p class="size">When the timer ends,</p>
          <p class="size">you'll begin recording.</p>
        </div>
        <div id="timer-display">00:00/00:10</div>
        <div class="progress-bar">
          <div class="progress" id="progress"></div>
        </div>
        <button class="skip-btn" id="skipBtn">Skip</button>
      </div>

      <!-- Recording -->
      <div id="screen-recording" style="display: none">
        <p class="size">Record Your Reflection</p>
        <div class="status" id="record-status"></div>
        <div id="record-timer">00:00 / 03:00</div>
        <div class="progress-bar-recording">
          <div id="record-progress"></div>
        </div>
        <button id="recordBtn" class="start-record">Start recording</button>
      </div>
      <!-- Thank you -->
      <div id="screen-thankyou" style="display: none">
        <div class="background">
          <div class="guided-flow">
            <p class="size">Thank you</p>
            <div class="screen"></div>
            <p class="thankyou">We appreciate your</p>
            <p class="thankyou">time and reflection.</p>
          </div>
          <button class="button-down-colour" onclick="showScreen('welcome')">
            Start again
          </button>
        </div>
      </div>
    </div>
<!--start of JavaScript-->
<script>
  const tabs = {
    welcome: document.getElementById("tab-welcome"),
    waiver: document.getElementById("tab-waiver"),
    reflection: document.getElementById("tab-reflection"),
    recording: document.getElementById("tab-recording"),
    thankyou: document.getElementById("tab-thankyou"),
  };

  const screens = {
    welcome: document.getElementById("screen-welcome"),
    waiver: document.getElementById("screen-waiver"),
    reflection: document.getElementById("screen-reflection"),
    recording: document.getElementById("screen-recording"),
    thankyou: document.getElementById("screen-thankyou"),
  };

  let consentGiven = false;

  function setActiveTab(name) {
    Object.values(tabs).forEach((t) => t.classList.remove("active"));
    if (tabs[name]) tabs[name].classList.add("active");
  }

  function showScreen(name) {
    Object.values(screens).forEach((s) => (s.style.display = "none"));
    screens[name].style.display = "block";
    setActiveTab(name);

    if (name === "welcome") {
      document.getElementById("consentName").value = "";
      consentGiven = false;
      resetRecordingUI();
      stopSlideshow(); // ensure slideshow stops if going back
    }

    if (name === "thankyou") {
      setTimeout(() => {
        showScreen("welcome");
      }, 15000);
    }
  }

  function resetRecordingUI() {
    document.getElementById("recordBtn").textContent = "Start recording";
    document.getElementById("recordBtn").className = "start-record";
    document.getElementById("record-progress").style.width = "0%";
    document.getElementById("record-timer").textContent = "00:00 / 03:00";
  }

  function submitConsent() {
    const nameField = document.getElementById("consentName");
    if (!nameField.value.trim()) {
      alert("Please enter your name to consent.");
      return;
    }
    consentGiven = true;
    goToReflection(true);
  }

  function goToReflection(withConsent) {
    consentGiven = withConsent;
    showScreen("reflection");

    setTimeout(() => {
      startTimer();
    }, 5000);
  }

  function playBeep() {
    const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    const oscillator = audioCtx.createOscillator();
    const gainNode = audioCtx.createGain();

    oscillator.type = "sine"; 
    oscillator.frequency.setValueAtTime(1000, audioCtx.currentTime); 
    gainNode.gain.setValueAtTime(1, audioCtx.currentTime); 

    oscillator.connect(gainNode);
    gainNode.connect(audioCtx.destination);

    oscillator.start();
    oscillator.stop(audioCtx.currentTime + 0.5); 
  }

  // Reflection Timer
  let reflectionTime = 10;
  let remaining = reflectionTime;
  let timerInterval;
  const timerDisplay = document.getElementById("timer-display");
  const progressBar = document.getElementById("progress");

  function updateTimerDisplay() {
    let elapsed = reflectionTime - remaining;
    let minElapsed = String(Math.floor(elapsed / 60)).padStart(2, "0");
    let secElapsed = String(elapsed % 60).padStart(2, "0");
    let minTotal = String(Math.floor(reflectionTime / 60)).padStart(2, "0");
    let secTotal = String(reflectionTime % 60).padStart(2, "0");
    timerDisplay.textContent = `${minElapsed}:${secElapsed}/${minTotal}:${secTotal}`;
    progressBar.style.width = `${
      ((reflectionTime - remaining) / reflectionTime) * 100
    }%`;
  }

  function startTimer() {
    remaining = reflectionTime;
    updateTimerDisplay();
    clearInterval(timerInterval);

    playBeep();

    timerInterval = setInterval(() => {
      remaining--;
      updateTimerDisplay();
      if (remaining <= 0) {
        clearInterval(timerInterval);

        playBeep();

        setTimeout(() => {
          if (consentGiven) {
            showScreen("recording");
          } else {
            showScreen("thankyou");
          }
        }, 700); 
      }
    }, 1000);
  }

  document.getElementById("skipBtn").onclick = () => {
    if (consentGiven) {
      showScreen("recording");
    } else {
      showScreen("thankyou");
    }
  };

  // Recording
  let mediaRecorder;
  let audioChunks = [];
  let recordTimerInterval;
  let recordSeconds = 0;
  const maxRecordTime = 180;
  const recordProgress = document.getElementById("record-progress");

  function updateRecordTimer() {
  let elapsed = recordSeconds;
  let minElapsed = String(Math.floor(elapsed / 60)).padStart(2, "0");
  let secElapsed = String(elapsed % 60).padStart(2, "0"); // ✅ fixed
  let minTotal = String(Math.floor(maxRecordTime / 60)).padStart(2, "0");
  let secTotal = String(maxRecordTime % 60).padStart(2, "0");
  document.getElementById("record-timer").textContent =
    `${minElapsed}:${secElapsed} / ${minTotal}:${secTotal}`;
  recordProgress.style.width = `${(elapsed / maxRecordTime) * 100}%`;
}

// Slideshow cleanup
function stopSlideshow() {
  clearInterval(slideshowInterval);
  recordingScreen.style.backgroundImage = ""; 
}


  const recordingScreen = document.getElementById("screen-recording");
  
  const slideshowImages = [
  "img1.png",
  "img2.png",
  "img3.png",
  "img4.png",
  "img5.png",
  "img6.png",
  "img7.png",
  "img8.png",
  "img9.png",
  "img10.png",
  "img11.png",
  "img12.png",
  "img13.png",
  "img14.png",
  "img15.png"
];

  let slideshowIndex = 0;
  let slideshowInterval;

  function startSlideshow() {
    slideshowIndex = 0;
    recordingScreen.style.backgroundImage = `url('${slideshowImages[slideshowIndex]}')`;
    recordingScreen.style.backgroundSize = "cover";
    recordingScreen.style.backgroundPosition = "center";
    slideshowInterval = setInterval(() => {
      slideshowIndex = (slideshowIndex + 1) % slideshowImages.length;
      recordingScreen.style.backgroundImage = `url('${slideshowImages[slideshowIndex]}')`;
    }, 15000); // change every 15 seconds
  }

  function stopSlideshow() {
    clearInterval(slideshowInterval);
  }

  document.getElementById("recordBtn").onclick = async () => {
    if (!mediaRecorder || mediaRecorder.state === "inactive") {
      try {
        const stream = await navigator.mediaDevices.getUserMedia({ audio: true });

        let options = {};
        if (MediaRecorder.isTypeSupported("audio/wav")) options = { mimeType: "audio/wav" };
        else if (MediaRecorder.isTypeSupported("audio/mp3")) options = { mimeType: "audio/mp3" };
        else if (MediaRecorder.isTypeSupported("audio/ogg")) options = { mimeType: "audio/ogg" };
        else options = { mimeType: "audio/webm" };

        mediaRecorder = new MediaRecorder(stream, options);
        audioChunks = [];
        mediaRecorder.ondataavailable = (e) => audioChunks.push(e.data);

        mediaRecorder.onstop = () => {
          const blob = new Blob(audioChunks, { type: mediaRecorder.mimeType });
          const url = URL.createObjectURL(blob);
          const a = document.createElement("a");
          a.href = url;
          let ext = "webm";
          if (mediaRecorder.mimeType.includes("wav")) ext = "wav";
          else if (mediaRecorder.mimeType.includes("mp3")) ext = "mp3";
          else if (mediaRecorder.mimeType.includes("ogg")) ext = "ogg";
          let consentName = document.getElementById("consentName").value.trim() || "Anonymous";
          consentName = consentName.replace(/[^a-z0-9]/gi, "_");
          const now = new Date();
          const utcTimestamp = now.toISOString().replace(/[:]/g, "-");
          a.download = `${consentName}_${utcTimestamp}.${ext}`;
          a.click();
          stream.getTracks().forEach((track) => track.stop());

          setTimeout(() => {
            showScreen("thankyou");
          }, 5000);
        };

        mediaRecorder.start();
        document.getElementById("recordBtn").textContent = "Stop recording";
        document.getElementById("recordBtn").className = "stop-record";
        recordSeconds = 0;
        updateRecordTimer();
        recordTimerInterval = setInterval(() => {
          recordSeconds++;
          updateRecordTimer();
          if (recordSeconds >= maxRecordTime) stopRecording();
        }, 1000);

        // start slideshow background when recording begins
        startSlideshow();

      } catch (err) {
        console.error("Error accessing microphone:", err);
        alert("Could not access your microphone. Please check permissions.");
      }
    } else {
      stopRecording();
    }
  };

  function stopRecording() {
    if (mediaRecorder && mediaRecorder.state !== "inactive") {
      mediaRecorder.stop();
    }
    clearInterval(recordTimerInterval);
    stopSlideshow(); // stop background slideshow when recording ends
  }

  updateTimerDisplay();
  showScreen("welcome");
</script>

</body>
</html>
