<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>امتحان أونلاين</title>
    <style>
        body {
            font-family: 'Tahoma', sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            direction: rtl;
        }
        .container {
            width: 60%;
            margin: auto;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.2);
            text-align: right;
        }
        h2 {
            text-align: center;
            color: #2c3e50;
        }
        .question {
            background: #ecf0f1;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            font-weight: bold;
        }
        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-top: 10px;
        }
        .option {
            padding: 10px;
            background-color: #d7dde0;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }
        .option:hover, .selected {
            background-color: #2980b9;
            color: white;
        }
        #result {
            font-size: 18px;
            font-weight: bold;
            color: #27ae60;
            text-align: center;
            margin-top: 20px;
        }
        #login {
            display: block;
            background: #2c3e50;
            color: white;
            padding: 30px;
            border-radius: 10px;
        }
        #login input {
            padding: 10px;
            border-radius: 5px;
            border: none;
            width: 80%;
            margin-bottom: 10px;
        }
        #login button {
            padding: 10px 20px;
            background: #27ae60;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background 0.3s;
        }
        #login button:hover {
            background: #219150;
        }
        #exam {
            display: none;
        }
        button#finish {
            padding: 12px 25px;
            background: #e74c3c;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
            margin-top: 20px;
            transition: background 0.3s;
        }
        button#finish:hover {
            background: #c0392b;
        }
    </style>
</head>
<body>
    <div class="container" id="login">
        <h2>تسجيل الدخول</h2>
        <p>يرجى إدخال اسمك والكود للمتابعة:</p>
        <input type="text" id="studentName" placeholder="أدخل اسمك">
        <input type="password" id="accessCode" placeholder="أدخل الكود">
        <button onclick="checkLogin()">دخول</button>
        <p id="error" style="color: red; display: none;">الكود غير صحيح!</p>
    </div>

    <div class="container" id="exam">
        <h2>امتحان في الفيزياء</h2>
        <div id="quiz"></div>
        <button id="finish" onclick="showResult()">إنهاء الامتحان</button>
        <div id="result" style="display:none;"></div>
    </div>

    <script>
const correctCode = "2526";
let studentName = "";
let score = 0;

function checkLogin() {
    let inputCode = document.getElementById("accessCode").value;
    studentName = prompt("يرجى إدخال اسمك:");
    if (inputCode === correctCode && studentName) {
        document.getElementById("login").style.display = "none";
        document.getElementById("exam").style.display = "block";
    } else {
        document.getElementById("error").style.display = "block";
    }
}

const questions = [
    { question: "ما وحدة قياس القوة؟", options: ["نيوتن", "جول", "واط", "أوم"], answer: "نيوتن" },
    { question: "ما هي سرعة الضوء؟", options: ["300,000 كم/ث", "150,000 كم/ث", "100,000 كم/ث", "50,000 كم/ث"], answer: "300,000 كم/ث" }
];

function loadQuestions() {
    let quizDiv = document.getElementById("quiz");
    quizDiv.innerHTML = "";
    questions.forEach((q, i) => {
        let questionDiv = document.createElement("div");
        questionDiv.classList.add("question");
        questionDiv.innerHTML = `<p>${i + 1}. ${q.question}</p>`;
        let optionsDiv = document.createElement("div");
        optionsDiv.classList.add("options");
        q.options.forEach(option => {
            let btn = document.createElement("button");
            btn.classList.add("option");
            btn.innerText = option;
            btn.onclick = () => selectOption(btn, i, option);
            optionsDiv.appendChild(btn);
        });
        questionDiv.appendChild(optionsDiv);
        quizDiv.appendChild(questionDiv);
    });
}

function selectOption(btn, index, option) {
    let options = btn.parentNode.querySelectorAll("button");
    options.forEach(opt => opt.classList.remove("selected"));
    btn.classList.add("selected");
    checkAnswer(index, option);
}

function checkAnswer(index, option) {
    if (option === questions[index].answer) {
        score++;
    }
}

function showResult() {
    document.getElementById("quiz").style.display = "none";
    document.querySelector("#finish").style.display = "none";
    let resultDiv = document.getElementById("result");
    resultDiv.style.display = "block";
    resultDiv.innerHTML = `<h3>لقد أكملت الامتحان!</h3><p>درجتك: ${score} من ${questions.length}</p>`;
    sendResultToSheet();
}

function sendResultToSheet() {
    const scriptURL = "https://script.google.com/macros/s/AKfycbwSScQmlz-SiAqkP-4WarxHkvyZ4RhE_mQUPKiIoknmKg-vydQpewDUIaCaWIHzZwcT/exec";

function checkLogin() {
    let inputCode = document.getElementById("accessCode").value;
    const correctCode = "2526";
    if (inputCode === correctCode) {
        document.getElementById("login").style.display = "none";
        document.getElementById("exam").style.display = "block";
    } else {
        document.getElementById("error").style.display = "block";
    }
}

function showResult() {
    document.getElementById("quiz").style.display = "none";
    document.querySelector("#finish").style.display = "none";
    let resultDiv = document.getElementById("result");
    resultDiv.style.display = "block";
    
    let studentName = prompt("أدخل اسمك:");
    if (!studentName) {
        alert("يجب إدخال الاسم!");
        return;
    }
    
    let scoreText = `لقد أكملت الامتحان! درجتك: ${score} من ${questions.length}`;
    resultDiv.innerHTML = `<h3>${scoreText}</h3>`;
    
    // إرسال البيانات إلى Google Sheets
    fetch(scriptURL, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ name: studentName, score: score, total: questions.length })
    })
    .then(response => response.text())
    .then(data => console.log("تم إرسال البيانات بنجاح: ", data))
    .catch(error => console.error("خطأ في الإرسال: ", error));
}


loadQuestions();

    </script>
