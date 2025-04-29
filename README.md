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
      "별 (ほし)": "호시",
      "계절 (きせつ)": "키세츠",
      "가격, 값 (かかく)": "카카쿠",
      "소개 (しょうかい)": "쇼-카이",
      "형제 (きょうだい)": "쿄-다이",
      "싸움 (けんか)": "켄카",
      "약속 (やくそく)": "야쿠소쿠",
      "설명 (せつめい)": "세츠메이",
      "경찰 (けいさつ)": "케-사츠",
      "산책 (さんぽ)": "삼포",
      "영어 (えいご)": "에-고",
      "외국 (がいこく)": "가이코쿠",
      "관광 (かんこう)": "칸코-",
      "지금 (いま)": "이마",
      "걱정 (しんぱい)": "심빠이",
      "꿈 (ゆめ)": "유메",
      "생활 (せいかつ)": "세-카츠",
      "구름 (くも)": "쿠모",
      "예정 (よてい)": "요테이",
      "최근 (さいきん)": "사이킨",
      "말, 언어 (ことば)": "코토바",
      "경험 (けいけん)": "케-켄",
      "진심 (ほんしん)": "혼신",
      "진심 (ほんき)": "혼키",
      "최후 (さいご)": "사이고",
      "모자 (ぼうし)": "보-시",
      "정말 (ほんとう)": "혼토-",
      "편리 (べんり)": "벤리",
      "잊은 물건 (わすれもの)": "와스레모노",
      "관계 (かんけい)": "칸케이",
      "경제 (けいざい)": "케-자이",
      "정치 (せいじ)": "세-지",
      "국제 (こくさい)": "코쿠사이",
      "간단 (かんたん)": "칸탄",
      "옛날 (むかし)": "무카시",
      "소설 (しょうせつ)": "쇼-세츠",
      "방해 (じゃま)": "쟈마",
      "경치 (けしき)": "케시키",
      "실내 (しつない)": "시츠나이",
      "선배 (せんぱい)": "선빠이",
      "전국 (ぜんこく)": "젠코쿠",
      "청소 (そうじ)": "소-지",
      "준비 (じゅんび)": "쥼비",
      "용의 (ようい)": "요-이",
      "상담 (そうだん)": "소-단",
      "힘 (ちから)": "치카라",
      "주소 (じゅうしょ)": "쥬-쇼",
      "아내 (つま)": "츠마",
      "운동 (うんどう)": "운도-",
      "끝 (おわり)": "오와리",
      "공기 (くうき)": "쿠-키"
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
