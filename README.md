<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>일본어 단어 퀴즈</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 40px;
    }
    h1 {
      font-size: 2rem;
    }
    .word {
      font-size: 2rem;
      margin: 20px;
    }
    input, button {
      font-size: 1.2rem;
      padding: 10px;
      margin: 10px;
    }
    .result {
      font-size: 1.2rem;
      margin-top: 20px;
    }
    .question-number {
      font-size: 1rem;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <h1>일본어 단어 퀴즈</h1>
  <div class="question-number" id="questionNumber"></div>
  <div class="word" id="question"></div>
  <input type="text" id="answer" placeholder="발음을 입력하세요" />
  <div>
    <button onclick="checkAnswer()">정답 확인</button>
    <button onclick="restartQuiz()">다시 시작</button>
  </div>
  <div class="result" id="result"></div>

  <script>
    const wordList = {
      "별": "호시",
      "계절": "키세츠",
      "가격, 값": "네단",
      "소개": "쇼-카이",
      "형제": "쿄-다이",
      "싸움": "켄카",
      "약속": "야쿠소쿠",
      "설명": "세츠메-",
      "경찰": "케-사츠",
      "산책": "산포",
      "영어": "에-고",
      "외국": "가이코쿠",
      "관광": "칸코-",
      "지금": "이마",
      "걱정": "신빠이",
      "꿈": "유메",
      "생활 ": "세-카츠",
      "구름": "쿠모",
      "예정": "요테-",
      "최근": "사이킨",
      "말, 언어": "코토바",
      "경험": "케-켄",
      "진심": "혼신",
      "최후": "사이고",
      "모자": "보-시",
      "정말": "혼토-",
      "편리": "벤리",
      "잊은 물건": "와스레모노",
      "관계": "칸케이",
      "경제": "케-자이",
      "정치": "세-지",
      "국제": "코쿠사이",
      "간단": "칸탄",
      "옛날": "무카시",
      "소설": "쇼-세츠",
      "방해": "쟈마",
      "경치": "케시키",
      "실내": "시츠나이",
      "선배": "선빠이",
      "전국": "젠코쿠",
      "청소": "소-지",
      "준비": "쥼비",
      "용의": "요-이",
      "상담": "소-단",
      "힘": "치카라",
      "주소": "쥬-쇼",
      "아내": "츠마",
      "운동": "운도-",
      "끝": "오와리",
      "공기": "쿠-키"
    };

    const koreanWords = Object.keys(wordList);
    let currentIndex = 0;
    let correctCount = 0;
    let isAnswered = false;

    function showQuestion() {
      if (currentIndex < koreanWords.length) {
        document.getElementById('question').textContent = koreanWords[currentIndex];
        document.getElementById('questionNumber').textContent = `${currentIndex + 1} / ${koreanWords.length}`;
        document.getElementById('answer').value = "";
        document.getElementById('result').textContent = "";
        isAnswered = false;
      } else {
        showResult();
      }
    }

    function checkAnswer() {
      if (isAnswered) return;
      const userAnswer = document.getElementById('answer').value.trim();
      const correctAnswer = wordList[koreanWords[currentIndex]];
      const resultDiv = document.getElementById('result');
      if (userAnswer === correctAnswer) {
        resultDiv.textContent = "정답입니다!";
        resultDiv.style.color = "blue";
        correctCount++;
      } else {
        resultDiv.textContent = `틀렸습니다. 정답은 '${correctAnswer}'입니다.`;
        resultDiv.style.color = "red";
      }
      isAnswered = true;
      setTimeout(() => {
        currentIndex++;
        showQuestion();
      }, 2000);
    }

    function restartQuiz() {
      currentIndex = 0;
      correctCount = 0;
      showQuestion();
    }

    function showResult() {
      alert(`퀴즈 종료!\n맞춘 개수: ${correctCount} / ${koreanWords.length}\n점수: ${correctCount}점`);
      restartQuiz();
    }

    showQuestion();
  </script>
</body>
</html>

