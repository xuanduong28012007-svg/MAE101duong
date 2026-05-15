<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Đề Thi Trắc Nghiệm Hàm Số</title>

  <!-- MathJax -->
  <script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f9;
      padding: 20px;
      line-height: 1.6;
    }

    h1 {
      text-align: center;
      color: #1e3a8a;
    }

    .question-box {
      background: white;
      padding: 20px;
      margin-bottom: 20px;
      border-radius: 12px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }

    .question {
      font-weight: bold;
      margin-bottom: 15px;
      font-size: 18px;
    }

    .option {
      display: block;
      background: #e5e7eb;
      padding: 10px;
      margin: 8px 0;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }

    .option:hover {
      background: #d1d5db;
    }

    .correct {
      background: #22c55e !important;
      color: white;
    }

    .wrong {
      background: #ef4444 !important;
      color: white;
    }

    .disabled {
      pointer-events: none;
    }

    .answer {
      margin-top: 10px;
      padding: 10px;
      border-left: 5px solid #2563eb;
      background: #eff6ff;
      display: none;
      border-radius: 6px;
    }

    .score-box {
      text-align: center;
      font-size: 24px;
      margin-top: 30px;
      font-weight: bold;
      color: #1d4ed8;
    }
  </style>
</head>

<body>

<h1>ĐỀ THI TRẮC NGHIỆM HÀM SỐ</h1>

<div id="quiz"></div>

<div class="score-box" id="scoreBox">
  Điểm: 0 / 15
</div>

<script>
const questions = [
{
  q: "Miền xác định của hàm số \\( y = \\dfrac{1}{x-2} \\) là:",
  options: [
    "\\( \\mathbb{R} \\)",
    "\\( \\mathbb{R} \\setminus \\{2\\} \\)",
    "\\( \\mathbb{R} \\setminus \\{0\\} \\)",
    "\\( x > 2 \\)"
  ],
  answer: 1,
  explain: "Mẫu số phải khác 0 nên \\(x-2 \\neq 0 \\Rightarrow x \\neq 2\\)."
},

{
  q: "Miền xác định của hàm số \\( y = \\sqrt{x-1} \\) là:",
  options: [
    "\\( x \\ge 1 \\)",
    "\\( x > 1 \\)",
    "\\( x \\le 1 \\)",
    "\\( \\mathbb{R} \\)"
  ],
  answer: 0,
  explain: "Biểu thức trong căn phải không âm nên \\(x-1 \\ge 0\\Rightarrow x \\ge 1\\)."
},

{
  q: "Hàm số \\(f(x)=x^2\\) là:",
  options: [
    "Hàm lẻ",
    "Không chẵn không lẻ",
    "Hàm chẵn",
    "Không xác định"
  ],
  answer: 2,
  explain: "\\(f(-x)=(-x)^2=x^2=f(x)\\) nên là hàm chẵn."
},

{
  q: "Hàm số \\(f(x)=x^3\\) là:",
  options: [
    "Hàm chẵn",
    "Hàm lẻ",
    "Không chẵn không lẻ",
    "Không xác định"
  ],
  answer: 1,
  explain: "\\(f(-x)=(-x)^3=-x^3=-f(x)\\) nên là hàm lẻ."
},

{
  q: "Miền giá trị của hàm số \\( y=x^2 \\) là:",
  options: [
    "\\( y \\ge 0 \\)",
    "\\( y > 0 \\)",
    "\\( y \\le 0 \\)",
    "\\( \\mathbb{R} \\)"
  ],
  answer: 0,
  explain: "Bình phương mọi số thực luôn không âm."
},

{
  q: "Đường cong nào sau đây là đồ thị của một hàm số?",
  options: [
    "Đường tròn",
    "Parabol \\(y=x^2\\)",
    "Đường thẳng đứng",
    "Hình elip"
  ],
  answer: 1,
  explain: "Parabol thỏa mãn kiểm tra đường thẳng đứng nên là đồ thị hàm số."
},

{
  q: "Đồ thị nào KHÔNG phải là đồ thị hàm số?",
  options: [
    "\\(y=2x+1\\)",
    "\\(y=|x|\\)",
    "Đường tròn \\(x^2+y^2=1\\)",
    "\\(y=x^3\\)"
  ],
  answer: 2,
  explain: "Một giá trị x có thể có 2 giá trị y nên không phải hàm số."
},

{
  q: "Miền xác định của hàm số \\( y = \\dfrac{1}{\\sqrt{x-3}} \\) là:",
  options: [
    "\\(x>3\\)",
    "\\(x\\ge3\\)",
    "\\(x<3\\)",
    "\\(\\mathbb{R}\\)"
  ],
  answer: 0,
  explain: "Vì căn ở mẫu nên \\(x-3>0\\Rightarrow x>3\\)."
},

{
  q: "Hàm số nào sau đây là hàm chẵn?",
  options: [
    "\\(f(x)=x^3+x\\)",
    "\\(f(x)=x^4+1\\)",
    "\\(f(x)=x+1\\)",
    "\\(f(x)=\\sqrt{x}\\)"
  ],
  answer: 1,
  explain: "\\(f(-x)=(-x)^4+1=x^4+1=f(x)\\)."
},

{
  q: "Hàm số nào sau đây là hàm lẻ?",
  options: [
    "\\(f(x)=x^2+1\\)",
    "\\(f(x)=x^3-x\\)",
    "\\(f(x)=|x|\\)",
    "\\(f(x)=x^2\\)"
  ],
  answer: 1,
  explain: "\\(f(-x)=-x^3+x=-(x^3-x)=-f(x)\\)."
},

{
  q: "Miền giá trị của hàm số \\( y=\\sqrt{x} \\) là:",
  options: [
    "\\( y>0 \\)",
    "\\( y\\ge0 \\)",
    "\\( y\\le0 \\)",
    "\\( \\mathbb{R} \\)"
  ],
  answer: 1,
  explain: "Căn bậc hai luôn không âm."
},

{
  q: "Hàm số \\( y=\\dfrac{x+1}{x^2+1} \\) có miền xác định là:",
  options: [
    "\\( x\\neq1 \\)",
    "\\( x\\neq-1 \\)",
    "\\( \\mathbb{R} \\)",
    "\\( x>0 \\)"
  ],
  answer: 2,
  explain: "Vì \\(x^2+1>0\\) với mọi x nên xác định trên toàn bộ \\(\\mathbb{R}\\)."
},

{
  q: "Đường thẳng đứng có phải đồ thị hàm số không?",
  options: [
    "Có",
    "Không",
    "Đôi khi",
    "Chỉ khi đi qua gốc tọa độ"
  ],
  answer: 1,
  explain: "Một giá trị x có vô số giá trị y nên không phải hàm số."
},

{
  q: "Miền giá trị của hàm số \\( y=-x^2 \\) là:",
  options: [
    "\\( y\\ge0 \\)",
    "\\( y\\le0 \\)",
    "\\( \\mathbb{R} \\)",
    "\\( y>0 \\)"
  ],
  answer: 1,
  explain: "Vì \\(-x^2\\le0\\) với mọi x."
},

{
  q: "Hàm số \\(f(x)=2x^5\\) là:",
  options: [
    "Hàm chẵn",
    "Hàm lẻ",
    "Không chẵn không lẻ",
    "Không xác định"
  ],
  answer: 1,
  explain: "\\(f(-x)=2(-x)^5=-2x^5=-f(x)\\)."
}
];

const quiz = document.getElementById("quiz");
const scoreBox = document.getElementById("scoreBox");

let score = 0;

questions.forEach((item, index) => {
  const box = document.createElement("div");
  box.className = "question-box";

  let html = `
    <div class="question">
      Câu ${index + 1}: ${item.q}
    </div>
  `;

  item.options.forEach((opt, i) => {
    html += `
      <div class="option" onclick="checkAnswer(this, ${index}, ${i})">
        ${String.fromCharCode(65 + i)}. ${opt}
      </div>
    `;
  });

  html += `
    <div class="answer" id="answer-${index}">
      <strong>Đáp án đúng:</strong> ${String.fromCharCode(65 + item.answer)} <br>
      <strong>Giải thích:</strong> ${item.explain}
    </div>
  `;

  box.innerHTML = html;
  quiz.appendChild(box);
});

function checkAnswer(element, qIndex, selected) {
  const questionBox = element.parentElement;
  const options = questionBox.querySelectorAll(".option");
  const answerBox = document.getElementById(`answer-${qIndex}`);

  options.forEach(opt => opt.classList.add("disabled"));

  if (selected === questions[qIndex].answer) {
    element.classList.add("correct");
    score++;
  } else {
    element.classList.add("wrong");
    options[questions[qIndex].answer].classList.add("correct");
  }

  answerBox.style.display = "block";
  scoreBox.innerHTML = `Điểm: ${score} / 15`;

  MathJax.typeset();
}
</script>

</body>
</html>
