# probable-funicular
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>For My Love</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body, html {
      height: 100%;
      font-family: 'Segoe UI', sans-serif;
      background-color: #ffe6f0;
      overflow: hidden;
    }

    #questionPage, #letterPage {
      display: none;
      height: 100vh;
      width: 100%;
      position: absolute;
      top: 0;
      left: 0;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 20px;
      transition: all 1s ease-in-out;
    }

    #questionPage.active, #letterPage.active {
      display: flex;
      flex-direction: column;
      animation: fadeIn 2s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .question-box {
      background: white;
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
      max-width: 500px;
    }

    .question-text {
      font-size: 24px;
      margin-bottom: 20px;
      color: #d63384;
    }

    .btn {
      padding: 10px 20px;
      margin: 10px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      background-color: #ff99cc;
      color: white;
      cursor: pointer;
    }

    .btn:hover {
      background-color: #ff66b2;
    }

    #letterPage {
      background-color: #ffe6f0;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    #letter {
      max-width: 600px;
      background: white;
      padding: 30px;
      border-radius: 20px;
      font-size: 15px;
      color: #4b0038;
      line-height: 1.6;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
      position: relative;
    }

    /* Heart animation */
    .heart {
      width: 20px;
      height: 20px;
      position: absolute;
      background: red;
      transform: rotate(45deg);
      animation: float 4s infinite ease-in;
    }

    .heart::before,
    .heart::after {
      content: '';
      width: 20px;
      height: 20px;
      position: absolute;
      background: red;
      border-radius: 50%;
    }

    .heart::before {
      top: -10px;
      left: 0;
    }

    .heart::after {
      left: -10px;
      top: 0;
    }

    @keyframes float {
      0% {
        transform: translateY(0) rotate(45deg);
        opacity: 1;
      }
      100% {
        transform: translateY(-100vh) rotate(45deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div id="questionPage" class="active">
    <div class="question-box">
      <p class="question-text" id="question">Hi baby, I have a few questions for you. Please answer them, okay? 💕</p>
      <div id="buttons">
        <button class="btn" onclick="nextQuestion('Yes')">Yes</button>          
        <button class="btn" onclick="nextQuestion('No')">No</button>
      </div>
    </div>
  </div>

  <div id="letterPage">
    <div id="letter">
      <p>
        To the love of my life,<br><br>
        Hi love, happy monthsary po. Alam ko pong alam mo na sobrang mahal na mahal kita, pero gusto ko pa rin pong ulit ulitin sayo yung salitang mahal kita. Hindi ko man po maparamdam sayo ng sobra ang pagmamahal ko araw araw, pero sana po maramdaman mo pa rin yun sa mga simpleng ginagawa ko o pinaparamdam ko sayo. Sa paglipas po ng mga araw, mas lalo pa po kitang minamahal. Palagi ka pong nasa isip, puso, at panalangin ko. Ikaw po ang dahilan kung bakit ako masaya sa bawat araw at kung bakit po gumagaan ang lahat ng bagay para sakin. Sobrang nagpapasalamat po ako kasi nakilala ko yung sobrang ganda kong baby. Mahal ko, lagi mong tandaan na kahit gaano man tayo kalayo sa isat isa, nandito lang ako para sayo at hinding hindi kita iiwan. Ikaw lang at ikaw pa rin ang pipiliin ko araw araw, kahit gaano pa kahirap ang sitwasyon. Salamat kasi ikaw ang dahilan kung bakit mas gusto ko pang magsikap, magmahal, at mangarap. Iloveyousomuch, my baby. Happy monthsary ulit.💖<br><br>
        With all my love,<br>
        Ciara
      </p>
    </div>
    <audio autoplay loop>
      <source src="https://www.youtube.com/embed/5cKeDvaD5eI      " type="audio/mpeg">
    </audio>
  </div>

  <script>
    const questions = [
  "Do you love me?",
  "Do you feel happy when we talk?",
  "Will you stay with me forever?",
  "Do I make you feel special?",
  "Do you see a future with me?",
  "Do you feel safe with me?",
  "Would you choose me again and again?",
  "Do you enjoy our little moments together?",
  "Do I mean a lot to you?",
  "Do I make you feel loved?",
];


    let current = 0;
    const questionText = document.getElementById("question");

    function nextQuestion(answer) {
      // Optional: send answer to yourself
      console.log(`Answered: ${questions[current]} - ${answer}`);

      current++;
      if (current < questions.length) {
        questionText.textContent = questions[current];
      } else {
        // When done, show a button to go to letter
        document.getElementById("buttons").innerHTML = '<button class="btn" onclick="showLetter()">Continue to my message</button>';
        questionText.textContent = "Thank you for answering, baby 💖";
      }
    }

    function showLetter() {
      document.getElementById("questionPage").classList.remove("active");
      document.getElementById("letterPage").classList.add("active");
      generateHearts();
    }

    function generateHearts() {
      for (let i = 0; i < 30; i++) {
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.style.left = Math.random() * 100 + "%";
        heart.style.top = Math.random() * 100 + "%";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 4000);
      }
    }
  </script>
</body>
</html>

