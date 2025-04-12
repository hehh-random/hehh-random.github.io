<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>100 Taps of Reason I Love U 💖</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #fff0f5;
      color: #333;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      text-align: center;
      padding: 20px;
      overflow: hidden;
      transition: background-color 0.3s, color 0.3s;
    }

    h1 {
      font-size: 24px;
      margin-bottom: 20px;
      color: #e91e63;
    }

    #message {
      font-size: 20px;
      padding: 20px;
      max-width: 600px;
      min-height: 100px;
      background-color: #ffe4ec;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      margin-bottom: 20px;
      transition: background-color 0.3s, color 0.3s;
    }

    #counter {
      font-size: 18px;
      margin-bottom: 15px;
      color: #d81b60;
    }

    #tapBtn {
      background-color: #e91e63;
      color: white;
      padding: 12px 30px;
      border: none;
      border-radius: 30px;
      font-size: 18px;
      cursor: pointer;
      transition: 0.3s ease;
    }

    #tapBtn:hover {
      background-color: #d81b60;
    }

    /* Falling elements */
    .falling {
      position: absolute;
      top: -50px;
      font-size: 24px;
      pointer-events: none;
      animation: fall linear infinite;
    }

    @keyframes fall {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 0.8;
      }
      100% {
        transform: translateY(110vh) rotate(360deg);
        opacity: 0;
      }
    }

    /* Night Mode Styles */
    .night-mode {
      background-color: #333;
      color: #fff;
    }

    .night-mode #message {
      background-color: #444;
      color: #fff;
    }

    .night-mode #tapBtn {
      background-color: #333;
      color: #e91e63;
    }

    .night-mode #tapBtn:hover {
      background-color: #555;
    }

    .night-mode h1 {
      color: #ff4081;
    }
  </style>
</head>
<body>

  <h1>Tap to Reveal the message 💞</h1>
  <div id="message">Tap the button to see a message...</div>
  <div id="counter">You have tapped 0 out of 100 times.</div>
  <button id="tapBtn">Tap Me 💖</button>
  <button id="nightModeBtn" style="margin-top: 20px; padding: 10px 20px; background-color: #333; color: #fff; border: none; border-radius: 30px; cursor: pointer;">Night Mode</button>

  <!-- Falling elements: stars, hearts, spiderwebs -->
  <script>
    const symbols = ["🌚", "🕷", "🕸️"];
    const count = 40;

    for (let i = 0; i < count; i++) {
      const el = document.createElement("div");
      el.className = "falling";
      el.textContent = symbols[Math.floor(Math.random() * symbols.length)];
      el.style.left = `${Math.random() * 100}vw`;
      el.style.animationDuration = `${4 + Math.random() * 6}s`;
      el.style.animationDelay = `${Math.random() * 5}s`;
      el.style.fontSize = `${18 + Math.random() * 20}px`;
      document.body.appendChild(el);
    }
  </script>

  <script>
    const messages = [
      "Tum meri zindagi ki subah ho ",
      "Tumhari hasi jese raato ka chand ho ",
      "Tere bin sab kuch adhura lagta hai ",
      "Tujhse hi toh meri subha hota hai ",
      "Tum ho toh har pal suhana hai ",
      "Teri baato(bhaw bhaw) se hi toh asli maja hai ",
      "Tu hai toh mai hu ",
      "Teri aankho mai meri duniya hai ",
      "Tere saath waqt ka pta nhi chlta hai ",
      "Tera naam lena bhi pyaar lagta hai😏 ",
      "Tumhari har ada pyaari hai ",
      "Tuje hi har dua mai manga hai",
      "Tum meri khushi ki wajah ho ",
      "Tere saath hu toh lagta sab jannat hai ",
      "Tere bina sab bekaar lagta hai ",
      "Teri hassi meri jaan le leti hai ",
      "Tum meri calmness ho ",
      "uhm uhmm jada kush nhi hoiye ",
      "Tum meri har soch mai ho ",
      "Tera naam sunte hi smile aa jati hai ",
      "Tum meri energy ho ",
      "Tere saath har season special lagta hai ",
      "Tumse baat na ho toh din adhura hai ",
      "Tum ho toh sab kuch possible hai ",
      "Tere bina toh mai kuch bhi nahi ",
      "Tum meri favorite notification ho ",
      "Tujhse baat karna therapy jaisa lagta hai ",
      "Tum meri subha ki chai ho ",
      "Tum meri zindagi ka sweet part ho(mittha😏) ",
      "Teri har ek baat special hai ",
      "shat aapp ",
      "Tum mere sapno ka sach ho ",
      "Tere saath sab easy lagta hai ",
      "Tere bina waqt ruk jata hai ",
      "Tum meri har story ho ",
      "Tum mera toothbrush ho😂 ",
      "Tumhari smile jaan le leti h hai(ky mtlb jaanlewa ho) ",
      "Tere saath duniya jeet sakti hu ",
      "Tum ho toh andhera bhi roshani lagta hai ",
      "Tujhse milke sab theek ho gaya hai ",
      "Tum meri atma ka hissa ho(bhootni hu n mai esi liye) ",
      "Tum meri dil ki dadhkan ho ",
      "Tum bina zindagi soch nahi sakti ",
      "Tere saath har jagah mst hai ",
      "Tere bina khushi adhuri hai ",
      "Tum meri playlist ka fav singer ho ",
      "Tere saath har pal memory ban jata hai ",
      "Tum ho toh mai hu ",
      "Tumhara gussa bhi cute lagta hai😏 ",
      "Tumarhe sapne dekh ke dil garden garden ho jata hai🌚",
      "Tum jaisa koi nahi ",
      "Tere bina sab kuch khali hai ",
      "Tere bina main lost hoon ",
      "Tu meri shanti hai aur mai teri tufaan hu😂 ",
      "Tum ho toh sab kuch bole toh jhakas hai ",
      "Tum ho toh har problem solve ho jati hai ",
      "Tum mera 🫶 ho ",
      "Tu wo sapna hai toh reality se acha hai  ",
      "Tere bina raat bhi khali lagti hai 🌚",
      "Tum ho toh har raat sapna lagta hai ",
      "Tujhse baat karke din ban jata hai(raat bhi🌚) ",
      "Tum mere liye perfect ho ",
      "Tu meri life ka filter hai ",
      "Tum mere har song ki feeling ho ",
      "Tum meri comfort zone ho ",
      "Tum meri subha ka phela khayal ho ",
      "Tum ho toh pyaar hai ",
      "Tere bina koi maja nahi hai ",
      "Uhm jada padh liye ho (tapped count dekho) us when😂 ",
      "Tujhse milna sabse best moment tha ",
      "Tum ho toh duniya colorful lagti hai ",
      "Tumhari aankhen meri weakness hai(body bhi)🫠 ",
      "Tu meri life ka goal hai ",
      "Tere bina sab incomplete lagta hai ",
      "Tere saath waqt ud jata hai 🕊️(jese tu udh rha abhi) ",
      "Tum meri ek hi chahat ho 😏",
      "jada dant nhi phado kahi gir na jaye ",
      "Tum ho toh sab kuch khwab lagta hai ",
      "Tere saath sab kuch uhmm uhmm🌚 lagta hai ",
      "Tum mere liye ho special edition ",
      "Tum ho toh main best version hu ",
      "Tum bina din hai ",
      "Tumhara naam sabse sweet lagta hai(bikkyy)😂 ",
      "Tum meri zindagi ki roshni ho ",
      "Tere bina sapne bhi udasi laate hai ",
      "Tere saath hi toh jeevan suhana hai ",
      "Tum mere har plan ka part ho ",
      "Tere saath har movie perfect lagti hai(imagine kr leti apko) ",
      "Tum meri best notification ho ",
      "Tum ho toh har din special hai ",
      "Tum meri story ka part ho ",
      "Tum meri jaan ho(jaanwar) ",
      "rest lelo bhaiya todha ",
      "uhm uhm udh toh nhi gye aap ",
      "Tum ho toh har pal mehfil hai ",
      "Tum meri har shayari ka subject ho (shayari ati nhi pr fhir bhi) ",
      "Tum meri zindagi ka screenshot ho ",
      "Tum mere raat ke chand ho ",
      "Tujhse baat karke sab tension chala jaata hai ",
      "Tum mere liye priceless ho ",
      "Tumhara naam se hi hass deti hu ",
      "Tum meri aakhri aur sabse khoobsurat love story ho ",
    ];
    messages.push(" LOVE YOUUU BKL😏🫶 uhmm kesaa lagaa sir jiii ");

    let index = 0;
    const btn = document.getElementById("tapBtn");
    const msgDiv = document.getElementById("message");
    const counter = document.getElementById("counter");

    btn.addEventListener("click", () => {
      if (index < messages.length) {
        msgDiv.textContent = messages[index];
        index++;
        counter.textContent = `You have tapped ${index} out of 100 times.`;
        if (index === messages.length) {
          btn.style.display = "none";
        }
      }
    });

    // Night Mode Toggle
    const nightModeBtn = document.getElementById("nightModeBtn");
    nightModeBtn.addEventListener("click", () => {
      document.body.classList.toggle("night-mode");
      if (document.body.classList.contains("night-mode")) {
        nightModeBtn.textContent = "Light Mode";
      } else {
        nightModeBtn.textContent = "Night Mode";
      }
    });
  </script>
</body>
</html>
