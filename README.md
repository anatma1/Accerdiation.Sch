<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>חידון הכנה לאקרדיטציה | היחידה לתזונה - מרכז שניידר</title>
  <link href="https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg-gradient: linear-gradient(135deg, #eef7f4 0%, #f3f7fc 50%, #fdf6ee 100%);
      --card-bg: #ffffff;
      --primary: #2b7a78;
      --primary-light: #def2f1;
      --accent: #3aafa9;
      --peach: #fceade;
      --yellow-soft: #fff9db;
      --text-main: #1f2d3d;
      --text-muted: #5c6b7a;
      --correct-bg: #e6f7ed;
      --correct-border: #2e9e5b;
      --wrong-bg: #fdecea;
      --wrong-border: #d93025;
      --shadow: 0 10px 28px rgba(31, 45, 61, 0.08);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Rubik', sans-serif;
    }

    body {
      background: var(--bg-gradient);
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .container {
      width: 100%;
      max-width: 540px;
      background: var(--card-bg);
      border-radius: 24px;
      box-shadow: var(--shadow);
      padding: 24px 20px;
      border: 1px solid rgba(43, 122, 120, 0.12);
    }

    .header {
      text-align: center;
      margin-bottom: 18px;
    }

    .badge {
      display: inline-block;
      background: var(--primary-light);
      color: var(--primary);
      font-size: 0.82rem;
      font-weight: 600;
      padding: 5px 14px;
      border-radius: 999px;
      margin-bottom: 8px;
    }

    h1 {
      font-size: 1.38rem;
      color: var(--primary);
      font-weight: 700;
      line-height: 1.3;
    }

    .subtitle {
      font-size: 0.9rem;
      color: var(--text-muted);
      margin-top: 4px;
    }

    .progress-wrap {
      margin: 16px 0 20px;
    }

    .progress-info {
      display: flex;
      justify-content: space-between;
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--text-muted);
      margin-bottom: 6px;
    }

    .progress-bar {
      width: 100%;
      height: 10px;
      background: #e9eff5;
      border-radius: 999px;
      overflow: hidden;
    }

    .progress-fill {
      height: 100%;
      width: 10%;
      background: linear-gradient(90deg, var(--primary), var(--accent));
      border-radius: 999px;
      transition: width 0.35s ease;
    }

    .question-topic {
      font-size: 0.82rem;
      font-weight: 600;
      color: #8a5a44;
      background: var(--peach);
      display: inline-block;
      padding: 4px 12px;
      border-radius: 10px;
      margin-bottom: 10px;
    }

    .question-text {
      font-size: 1.08rem;
      font-weight: 600;
      line-height: 1.45;
      margin-bottom: 16px;
      color: var(--text-main);
    }

    .options {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .option-btn {
      width: 100%;
      text-align: right;
      background: #f8fafc;
      border: 2px solid #e2e8f0;
      border-radius: 14px;
      padding: 13px 15px;
      font-size: 0.95rem;
      line-height: 1.4;
      color: var(--text-main);
      cursor: pointer;
      transition: all 0.2s ease;
      display: flex;
      align-items: flex-start;
      gap: 10px;
    }

    .option-btn:hover:not(:disabled) {
      background: var(--primary-light);
      border-color: var(--accent);
    }

    .option-letter {
      font-weight: 700;
      color: var(--primary);
      min-width: 22px;
    }

    .option-btn.correct {
      background: var(--correct-bg);
      border-color: var(--correct-border);
      color: #165b33;
      font-weight: 500;
    }

    .option-btn.wrong {
      background: var(--wrong-bg);
      border-color: var(--wrong-border);
      color: #8c1d18;
    }

    .option-btn:disabled {
      cursor: default;
    }

    .explanation-box {
      margin-top: 16px;
      padding: 14px 16px;
      border-radius: 14px;
      background: var(--yellow-soft);
      border-right: 4px solid #e6b800;
      font-size: 0.92rem;
      line-height: 1.5;
      display: none;
      box-shadow: 0 4px 12px rgba(230, 184, 0, 0.12);
    }

    .explanation-box.show {
      display: block;
      animation: popIn 0.28s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }

    .next-btn, .action-btn {
      width: 100%;
      margin-top: 18px;
      padding: 14px;
      border: none;
      border-radius: 14px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: transform 0.15s ease, opacity 0.2s ease;
    }

    .next-btn {
      background: var(--primary);
      color: #fff;
      display: none;
    }

    .next-btn.show {
      display: block;
    }

    .next-btn:hover, .action-btn:hover {
      opacity: 0.94;
      transform: translateY(-1px);
    }

    /* Result Screen */
    .result-screen {
      display: none;
      text-align: center;
    }

    .result-screen.show {
      display: block;
      animation: fadeIn 0.35s ease;
    }

    .score-circle {
      width: 124px;
      height: 124px;
      border-radius: 50%;
      background: var(--primary-light);
      border: 5px solid var(--primary);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin: 12px auto 16px;
    }

    .score-num {
      font-size: 2rem;
      font-weight: 700;
      color: var(--primary);
      line-height: 1.1;
    }

    .score-sub {
      font-size: 0.85rem;
      color: var(--text-muted);
      font-weight: 500;
    }

    .feedback-card {
      background: #f4fbf9;
      border: 2px solid var(--primary-light);
      border-radius: 18px;
      padding: 18px 16px;
      margin-bottom: 18px;
    }

    .feedback-emoji {
      font-size: 2.5rem;
      margin-bottom: 8px;
    }

    .feedback-text {
      font-size: 1.08rem;
      font-weight: 600;
      line-height: 1.45;
      color: var(--text-main);
    }

    .wa-btn {
      background: #25D366;
      color: #ffffff;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      text-decoration: none;
    }

    .retry-btn {
      background: #eef2f6;
      color: var(--text-main);
      margin-top: 10px;
    }

    footer {
      margin-top: 18px;
      text-align: center;
      font-size: 0.78rem;
      color: var(--text-muted);
    }

    @keyframes popIn {
      from { opacity: 0; transform: scale(0.96) translateY(6px); }
      to { opacity: 1; transform: scale(1) translateY(0); }
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(6px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <div class="container">
    <div class="header">
      <div class="badge">היחידה לתזונה • מרכז שניידר</div>
      <h1>חידון מוכנות לאקרדיטציה</h1>
      <div class="subtitle">10 שאלות קצרות שיכינו אתכן לבקרה בראש שקט</div>
    </div>

    <!-- Quiz View -->
    <div id="quiz-view">
      <div class="progress-wrap">
        <div class="progress-info">
          <span id="q-counter">שאלה 1 מתוך 10</span>
          <span id="score-live">ניקוד: 0</span>
        </div>
        <div class="progress-bar">
          <div class="progress-fill" id="progress-fill"></div>
        </div>
      </div>

      <div class="question-topic" id="q-topic"></div>
      <div class="question-text" id="q-text"></div>
      <div class="options" id="options-container"></div>
      <div class="explanation-box" id="explanation-box"></div>
      <button class="next-btn" id="next-btn" onclick="nextQuestion()">לשאלה הבאה ←</button>
    </div>

    <!-- Result View -->
    <div class="result-screen" id="result-view">
      <div class="score-circle">
        <div class="score-num" id="final-score-100">100</div>
        <div class="score-sub" id="final-score-10">10 מתוך 10</div>
      </div>

      <div class="feedback-card">
        <div class="feedback-emoji" id="feedback-emoji">🦚</div>
        <div class="feedback-text" id="feedback-text"></div>
      </div>

      <button class="action-btn wa-btn" onclick="shareWhatsApp()">
        <span>📲 שתפי חברה מהיחידה בוואטסאפ</span>
      </button>
      <button class="action-btn retry-btn" onclick="restartQuiz()">
        <span>🔄 שחקי שוב</span>
      </button>
    </div>
  </div>

  <footer>
    © כל הזכויות שמורות לענת מסלנסקי - דיאטנית קלינית. מרכז שניידר.
  </footer>

  <script>
    const questions = [
      {
        topic: "זיהוי מטופל (IPSG 01)",
        question: "את ניגשת למטופל כדי לתת הדרכה תזונתית. כיצד תבצעי זיהוי נכון?",
        options: [
          "שם מלא של הילד ושם ההורה",
          "שם מלא של הילד ות.ז",
          "שם ההורה ומקום לידה",
          "ת.ז ועיר מגורים"
        ],
        correct: 1,
        explanation: "זיהוי מטופל נעשה באמצעות 2 מזהים — שם מלא ומספר תעודת זהות. יש לבקש מהמטופל או מההורה לומר את הפרטים בעצמם באופן יזום (אסור להקריא להם ולבקש אישור) ולהשוות לצמיד הזיהוי."
      },
      {
        topic: "סוגי צמידים",
        question: "הבחנת בצמיד ירוק על ידו של מטופל במהלך ביקור הדיאטנית. מה משמעות הצמיד?",
        options: [
          "למטופל יש רגישות קשה לתרופות",
          "למטופל יש גפה בסיכון",
          "למטופל יש רגישות למזון (ללא פרטים מזהים)",
          "המטופל מאושפז במלר\"ד"
        ],
        correct: 2,
        explanation: "צמיד ירוק מסמן רגישות למזון (נענד בנוסף לצמיד הזיהוי הרגיל). צמיד אדום הוא לרגישות לתרופות, וצמיד ורוד לגפה בסיכון."
      },
      {
        topic: "תקשורת בין צוותים (מודל ה.מ.ר.א.ה)",
        question: "את מעבירה מידע לרופא המחלקה או לדיאטנית מחליפה לגבי מטופל. מה מייצגים ראשי התיבות ה.מ.ר.א.ה?",
        options: [
          "הערכה, מידע, רשומה, אבחנה, המשך טיפול",
          "הזמנה, מעקב, רגישויות, איסוף נתונים, הדרכה",
          "הזדהות, מצב, רקע, אומדן, המלצות",
          "הכנה, מדדים, רישום, אישור, העברה"
        ],
        correct: 2,
        explanation: "מודל ה.מ.ר.א.ה (ISBAR) מבטיח העברת מידע אחידה ובטוחה: הזדהות/הצגה, מצב נוכחי, רקע רפואי, אומדן עדכני והמלצות להמשך."
      },
      {
        topic: "זמני שמירת חלב אם",
        question: "כמה זמן מותר לשמור חלב אם (בטמפרטורת החדר / במקרר / במקפיא) לפי הנחיות היחידה?",
        options: [
          "טרי - שעתיים, במקרר - יומיים, במקפיא - חודשיים",
          "טרי - 3 שעות, במקרר - 3 ימים, במקפיא - 3 חודשים",
          "טרי - 4 שעות, במקרר - יומיים, במקפיא - 4 חודשים",
          "טרי - שעה אחת, במקרר - 24 שעות, במקפיא - חודש אחד"
        ],
        correct: 1,
        explanation: "כלל ה-3 שקל לזכור: 3 שעות בטמפרטורת החדר (טרי), 3 ימים במקרר, ו-3 חודשים במקפיא."
      },
      {
        topic: "סוגי בידוד והתנהגות",
        question: "את נכנסת לחדר של מטופל המאושפז בבידוד מגע (לדוגמה RSV או MRSA). מה נדרש ממך לבצע ולעטות?",
        options: [
          "מסכה כירורגית בלבד, והיגיינת ידיים ביציאה",
          "מסכת N95 ו-2 חלוקים זה על גבי זה",
          "היגיינת ידיים, חלוק אחד וכפפות",
          "כפפות בלבד, ללא חלוק וללא מסכה"
        ],
        correct: 2,
        explanation: "בכניסה לבידוד מגע נדרשים חיטוי/רחיצת ידיים, עטיית חלוק חד-פעמי וכפפות."
      },
      {
        topic: "יעדים בינלאומיים לבטיחות המטופל (IPSG)",
        question: "בבקרת האקרדיטציה נבחנת ההיכרות עם היעדים הבינלאומיים לבטיחות המטופל (IPSG). איזה מהבאים אינו נמנה עם יעדי ה-IPSG המרכזיים?",
        options: [
          "זיהוי מטופל באמצעות שני אמצעי זיהוי (IPSG 01)",
          "תקשורת בין מטפלים – Read Back ושימוש במודל ה.מ.ר.א.ה / ISBAR",
          "היגיינת ידיים בהתאם למודל חמשת הרגעים",
          "זמני שמירת חלב אם ופורמולות במקרר המחלקה"
        ],
        correct: 3,
        explanation: "יעדי ה-IPSG עוסקים בבטיחות המטופל ברמה הבינלאומית: זיהוי מטופל, תקשורת בין מטפלים, בטיחות בתרופות בסיכון גבוה, בטיחות בניתוחים ופעולות פולשניות, והיגיינת ידיים."
      },
      {
        topic: "אירוע סייבר",
        question: "הבחנת בשינוי חריג במסך המחשב או הודעה מוזרה הדורשת תשלום (\"מתקפת כופר\"). מהי הפעולה הראשונה שעליך לבצע?",
        options: [
          "לכבות את המחשב מהכפתור הראשי",
          "לנתק מיד את כבל התקשורת מהמחשב (בצד האחורי) ולדווח למוקד 4321",
          "לעשות הפעלה מחדש (Restart) כדי לראות אם זה נעלם",
          "להמשיך להקליד כרגיל ולקוות לטוב"
        ],
        correct: 1,
        explanation: "בחשד לאירוע סייבר חובה לנתק פיזית את כבל הרשת כדי למנוע את התפשטות הנגיף ברשת, ולדווח מיד למוקד 4321."
      },
      {
        topic: "טלפונים חשובים בעת חירום",
        question: "מהו מספר הטלפון המהיר להפעלת קוד החייאה במחלקה?",
        options: [
          "2222 ובנוסף 3232",
          "3232 ובנוסף 3000",
          "2222 ובנוסף 3000",
          "2222 ובנוסף 4321"
        ],
        correct: 2,
        explanation: "מחייגים 2222, ממתינים 2 שניות ואומרים פעמיים: \"החייאה במחלקה__, בניין__, קומה__ וחדר__\". בנוסף מחייגים 3000 לטיפול נמרץ (3232 הוא מוקד הביטחון ו-4321 הוא מוקד המחשוב)."
      },
      {
        topic: "סדר פעולות בעת גילוי אש",
        question: "מה מייצגים ראשי התיבות ד.ח.ו.פ בעת גילוי אש או עשן במחלקה?",
        options: [
          "דלתות סגורות, חילוץ מהיר, ויתור על ציוד, פינוי",
          "דיווח (למוקד 3232), חלץ (אנשים בסכנה), ונסה לכבות (במטף), פינוי",
          "דליקה, חנק, ויסות חמצן, פאניקה",
          "דיווח לאחות, חבישת מסכות, ונטילציה, פינוי"
        ],
        correct: 1,
        explanation: "ד.ח.ו.פ: דיווח למוקד 3232, חלץ אנשים מהאזור, ונסה לכבות (באמצעות מטף, אין להשתמש במים), פינוי בהתאם להנחיות."
      },
      {
        topic: "תקשורת ותרגום במשפחה שאינה דוברת עברית",
        question: "מהו סדר הפעולות הנכון כשנדרש לתת הדרכה תזונתית למשפחה שאינה דוברת עברית?",
        options: [
          "פנייה לבן משפחה לתרגום ← פנייה לאיש צוות מהרשימה של שניידר ← פנייה למוקד התרגום הטלפוני \"קול הבריאות\" (*5144)",
          "פנייה למוקד \"קול הבריאות\" (*5144) ← שימוש באפליקציית תרגום בנייד הפרטי ← פנייה לבן משפחה",
          "פנייה לאיש צוות מהרשימה של שניידר ← פנייה לבן משפחה ← שימוש בתנועות ידיים ואיורים",
          "שימוש ב-Google Translate ← פנייה למוקד 4321 ← זימון מתורגמן חיצוני"
        ],
        correct: 0,
        explanation: "סדר הפעולות הנכון הוא קודם כל היעזרות בבן משפחה, לאחר מכן פנייה לאיש צוות מתוך רשימת אנשי הצוות המסייעים בתרגום בפורטל שניידר (\"קישורים שימושיים\"), ובסוף פנייה למוקד התרגום הטלפוני \"קול הבריאות\" בחיוג *5144 (א'-ה' 08:00-20:00, ו' 08:00-13:00)."
      }
    ];

    const letters = ["א.", "ב.", "ג.", "ד."];
    let currentIdx = 0;
    let score = 0;
    let answered = false;

    function loadQuestion() {
      answered = false;
      const q = questions[currentIdx];
      document.getElementById("q-counter").textContent = `שאלה ${currentIdx + 1} מתוך ${questions.length}`;
      document.getElementById("score-live").textContent = `ניקוד: ${score * 10}`;
      document.getElementById("progress-fill").style.width = `${((currentIdx + 1) / questions.length) * 100}%`;
      document.getElementById("q-topic").textContent = q.topic;
      document.getElementById("q-text").textContent = q.question;

      const optionsContainer = document.getElementById("options-container");
      optionsContainer.innerHTML = "";

      q.options.forEach((opt, idx) => {
        const btn = document.createElement("button");
        btn.className = "option-btn";
        btn.innerHTML = `<span class="option-letter">${letters[idx]}</span><span>${opt}</span>`;
        btn.onclick = () => selectAnswer(idx);
        optionsContainer.appendChild(btn);
      });

      const expBox = document.getElementById("explanation-box");
      expBox.classList.remove("show");
      expBox.innerHTML = "";

      const nextBtn = document.getElementById("next-btn");
      nextBtn.classList.remove("show");
      nextBtn.textContent = currentIdx === questions.length - 1 ? "לסיכום והציון הסופי 🎉" : "לשאלה הבאה ←";
    }

    function selectAnswer(selectedIdx) {
      if (answered) return;
      answered = true;

      const q = questions[currentIdx];
      const buttons = document.querySelectorAll(".option-btn");

      buttons.forEach((btn, idx) => {
        btn.disabled = true;
        if (idx === q.correct) {
          btn.classList.add("correct");
        } else if (idx === selectedIdx) {
          btn.classList.add("wrong");
        }
      });

      const isCorrect = selectedIdx === q.correct;
      if (isCorrect) {
        score++;
        document.getElementById("score-live").textContent = `ניקוד: ${score * 10}`;
      }

      const expBox = document.getElementById("explanation-box");
      expBox.innerHTML = `<strong>${isCorrect ? "✅ תשובה נכונה!" : "❌ לא מדויק:"}</strong> ${q.explanation}`;
      expBox.classList.add("show");

      document.getElementById("next-btn").classList.add("show");
    }

    function nextQuestion() {
      currentIdx++;
      if (currentIdx < questions.length) {
        loadQuestion();
      } else {
        showResults();
      }
    }

    function showResults() {
      document.getElementById("quiz-view").style.display = "none";
      const resultView = document.getElementById("result-view");
      resultView.classList.add("show");

      const score100 = score * 10;
      document.getElementById("final-score-100").textContent = score100;
      document.getElementById("final-score-10").textContent = `${score} מתוך ${questions.length}`;

      let emoji = "";
      let text = "";

      if (score === 10) {
        emoji = "🦚";
        text = "אלופה! נשמח שתסתובבי כמו טווס בבית החולים ותעני על כל השאלות!";
      } else if (score >= 8) {
        emoji = "🌟";
        text = "מצוין! רואים שהתכוננת טוב לבקרה.";
      } else if (score >= 6) {
        emoji = "📖";
        text = "דרושה קריאה חוזרת של הטיפים.";
      } else {
        emoji = "😂";
        text = "עדיף שתיקחי חופש בשבוע הבא!";
      }

      document.getElementById("feedback-emoji").textContent = emoji;
      document.getElementById("feedback-text").textContent = text;
    }

    function shareWhatsApp() {
      const score100 = score * 10;
      const pageUrl = window.location.href.startsWith("http") ? `\nבואי לבדוק גם את עצמך: ${window.location.href}` : "";
      const msg = `היי! סיימתי את חידון ההכנה לאקרדיטציה של היחידה לתזונה בשניידר וקיבלתי ${score100} (${score}/10)! 🩺🥗${pageUrl}`;
      const waUrl = `https://api.whatsapp.com/send?text=${encodeURIComponent(msg)}`;
      window.open(waUrl, "_blank");
    }

    function restartQuiz() {
      currentIdx = 0;
      score = 0;
      document.getElementById("result-view").classList.remove("show");
      document.getElementById("quiz-view").style.display = "block";
      loadQuestion();
    }

    loadQuestion();
  </script>
</body>
</html>
