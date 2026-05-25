<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub бойынша интерактивті тест және Мониторинг</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f7f6;
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .test-container, .monitoring-container {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            max-width: 650px;
            width: 100%;
            margin-bottom: 30px;
        }
        h2, h3 { text-align: center; color: #24292e; }
        .input-group {
            margin-bottom: 25px;
        }
        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #333;
        }
        .input-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
            font-size: 16px;
        }
        .question {
            margin-bottom: 20px;
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
        }
        .question p {
            font-weight: 600;
            color: #24292e;
        }
        .options label {
            display: block;
            margin: 8px 0;
            cursor: pointer;
            padding: 8px;
            border-radius: 4px;
            transition: background 0.2s;
        }
        .options label:hover { background-color: #f0f0f0; }
        .options input { margin-right: 10px; }
        button {
            width: 100%;
            padding: 12px;
            background-color: #2ea44f;
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 18px;
            cursor: pointer;
            font-weight: bold;
        }
        button:hover { background-color: #2c974b; }
        
        /* Жеке оқушы нәтижесінің стильдері */
        #result {
            margin-top: 20px;
            padding: 20px;
            border-radius: 6px;
            display: none;
            font-size: 16px;
            line-height: 1.6;
            border: 1px solid #ccc;
            background-color: #fafbfc;
        }
        .stat-title { font-size: 20px; margin-bottom: 15px; border-bottom: 2px solid #24292e; padding-bottom: 5px; }
        .correct-ans { color: #155724; background-color: #d4edda; padding: 5px 10px; border-radius: 4px; margin: 5px 0; }
        .wrong-ans { color: #721c24; background-color: #f8d7da; padding: 5px 10px; border-radius: 4px; margin: 5px 0; }
        
        /* Мониторинг кестесінің стильдері */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: left;
        }
        th {
            background-color: #24292e;
            color: white;
        }
        tr:nth-child(even) { background-color: #f9f9f9; }
        .clear-btn {
            background-color: #cb2431;
            margin-top: 15px;
            font-size: 14px;
            padding: 8px;
        }
        .clear-btn:hover { background-color: #b31d28; }
    </style>
</head>
<body>

<div class="test-container">
    <h2>GitHub тақырыбы бойынша тест</h2>
    
    <div class="input-group">
        <label for="studentName">Жауап берушінің аты-жөні:</label>
        <input type="text" id="studentName" placeholder="Мысалы: Ахметов Әлішер" required>
    </div>

    <form id="quizForm">
        <div class="question">
            <p>1. GitHub платформасының басты қызметі қандай?</p>
            <div class="options">
                <label><input type="radio" name="q1" value="A"> А) Компьютерді вирустардан қорғау және тазалау</label>
                <label><input type="radio" name="q1" value="B"> Ә) Мектеп құжаттары мен электронды журналдарды толтыру</label>
                <label><input type="radio" name="q1" value="C"> Б) Бағдарламалық жасақтаманы (кодтарды) бірлесіп әзірлеу, сақтау және бақылау</label>
                <label><input type="radio" name="q1" value="D"> В) Тек қана хат алмасуға арналған әлеуметтік желі басқару</label>
            </div>
        </div>

        <div class="question">
            <p>2. Мәтіндегі "ойынды сақтап қою" (сохранение) метафорасы GitHub-тағы қай ұғымды түсіндіру үшін қолданылған?</p>
            <div class="options">
                <label><input type="radio" name="q2" value="A"> А) Repository (Репозиторий)</label>
                <label><input type="radio" name="q2" value="B"> Ә) Commit (Коммит)</label>
                <label><input type="radio" name="q2" value="C"> Б) Branch (Бұтақ)</label>
                <label><input type="radio" name="q2" value="D"> В) Pull Request (PR)</label>
            </div>
        </div>

        <div class="question">
            <p>3. Негізгі кодты бұзбай, жаңа идеяларды бөлек тексеріп көруге арналған параллельді жұмыс аймағы қалай аталады?</p>
            <div class="options">
                <label><input type="radio" name="q3" value="A"> А) Repository (Репозиторий)</label>
                <label><input type="radio" name="q3" value="B"> Ә) Commit (Коммит)</label>
                <label><input type="radio" name="q3" value="C"> Б) Branch (Бұтақ)</label>
                <label><input type="radio" name="q3" value="D"> В) Pull Request (PR)</label>
            </div>
        </div>

        <div class="question">
            <p>4. Мұғалімдерге тапсырмаларды автоматты түрде таратуға және тексеруге мүмкіндік беретін виртуалды сынып қалай аталады?</p>
            <div class="options">
                <label><input type="radio" name="q4" value="A"> А) GitHub Education</label>
                <label><input type="radio" name="q4" value="B"> Ә) GitHub Classroom</label>
                <label><input type="radio" name="q4" value="C"> Б) GitHub Pages</label>
                <label><input type="radio" name="q4" value="D"> В) GitHub Repository</label>
            </div>
        </div>

        <div class="question">
            <p>5. Мұғалімдер мен оқушыларға ешқандай хостинг сатып алмай-ақ, өздерінің жеке сайттарын (портфолио) тегін жариялауға мүмкіндік беретін құрал:</p>
            <div class="options">
                <label><input type="radio" name="q5" value="A"> А) GitHub Education</label>
                <label><input type="radio" name="q5" value="B"> Ә) GitHub Classroom</label>
                <label><input type="radio" name="q5" value="C"> Б) GitHub Pages</label>
                <label><input type="radio" name="q5" value="D"> В) GitHub Repository</label>
            </div>
        </div>

        <button type="button" onclick="checkQuiz()">Нәтижені тексеру</button>
    </form>

    <div id="result"></div>
</div>

<div class="monitoring-container">
    <h3>📊 Сынып мониторингі (Нәтижелер кестесі)</h3>
    <table id="resultsTable">
        <thead>
            <tr>
                <th>№</th>
                <th>Аты-жөні</th>
                <th>Нақты балл</th>
                <th>Пайыздық көрсеткіш</th>
            </tr>
        </thead>
        <tbody>
            </tbody>
    </table>
    <button class="clear-btn" onclick="clearMonitoring()">Кестені тазалау</button>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    updateTable();
});

function checkQuiz() {
    const nameInput = document.getElementById("studentName");
    const name = nameInput.value.trim();
    
    if (name === "") {
        alert("Өтініш, алдымен аты-жөніңізді енгізіңіз!");
        return;
    }

    const correctAnswers = { q1: "C", q2: "B", q3: "C", q4: "B", q5: "C" };
    const questionsText = {
        q1: "1-сұрақ (GitHub басты қызметі)",
        q2: "2-сұрақ ('Ойынды сақтау' метафорасы)",
        q3: "3-сұрақ (Параллельді жұмыс аймағы)",
        q4: "4-сұрақ (Виртуалды сынып)",
        q5: "5-сұрақ (Жеке сайттарды тегін жариялау)"
    };

    const form = document.getElementById("quizForm");
    
    if (!form.q1.value || !form.q2.value || !form.q3.value || !form.q4.value || !form.q5.value) {
        alert("Барлық сұраққа жауап беріңіз!");
        return;
    }

    let score = 0;
    let detailsHTML = `<div class="stat-title"><b>Тест нәтижесі:</b> ${name}</div>`;

    // Әр сұрақты жеке тексеріп, оқушы экранына есеп дайындау
    for (let i = 1; i <= 5; i++) {
        let qKey = "q" + i;
        let userAnswer = form[qKey].value;
        if (userAnswer === correctAnswers[qKey]) {
            score++;
            detailsHTML += `<div class="correct-ans">✅ ${questionsText[qKey]}: ДҰРЫС</div>`;
        } else {
            detailsHTML += `<div class="wrong-ans">❌ ${questionsText[qKey]}: ҚАТЕ (Сіздің жауабыңыз: ${userAnswer}, Дұрысы: ${correctAnswers[qKey]})</div>`;
        }
    }

    let percentage = (score / 5) * 100;
    detailsHTML += `<br><b>Жалпы балл:</b> ${score} / 5 (${percentage}%)`;

    // Оқушының экранына нәтижені шығару
    const resultDiv = document.getElementById("result");
    resultDiv.style.display = "block";
    resultDiv.innerHTML = detailsHTML;

    // Жалпы мониторинг базасына сақтау
    let monitoringData = JSON.parse(localStorage.getItem("github_quiz_results")) || [];
    monitoringData.push({ name: name, score: score, percent: percentage });
    localStorage.setItem("github_quiz_results", JSON.stringify(monitoringData));

    // Кестені жаңарту және форманы келесі оқушыға дайындау
    updateTable();
    form.reset();
    nameInput.value = "";
    
    // Экранды автоматты түрде нәтиже көрсетілген жерге жылжыту
    resultDiv.scrollIntoView({ behavior: 'smooth' });
}

function updateTable() {
    const tbody = document.querySelector("#resultsTable tbody");
    tbody.innerHTML = "";
    let monitoringData = JSON.parse(localStorage.getItem("github_quiz_results")) || [];
    
    monitoringData.forEach((student, index) => {
        let row = `<tr>
            <td>${index + 1}</td>
            <td>${student.name}</td>
            <td><b>${student.score}</b> / 5</td>
            <td>${student.percent}%</td>
        </tr>`;
        tbody.innerHTML += row;
    });
}

function clearMonitoring() {
    if (confirm("Барлық сыныптың мәліметін өшіргіңіз келе ме?")) {
        localStorage.removeItem("github_quiz_results");
        updateTable();
        document.getElementById("result").style.display = "none";
    }
}
</script>

</body>
</html>
