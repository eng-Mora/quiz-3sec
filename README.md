<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة الطلاب</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&display=swap');
        
        body { 
            font-family: 'Tajawal', sans-serif; 
            text-align: center; 
            direction: rtl; 
            background: linear-gradient(135deg, #3A1C71, #D76D77, #FFAF7B);
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }
        .container {
            width: 380px;
            padding: 40px;
            background: rgba(255, 255, 255, 0.95);
            color: #333;
            border-radius: 20px;
            box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.3);
            text-align: center;
            transition: 0.3s;
        }
        .container:hover {
            transform: scale(1.02);
        }
        h1 {
            font-size: 30px;
            color: #3A1C71;
            margin-bottom: 25px;
        }
        input {
            width: 100%;
            padding: 15px;
            margin: 15px 0;
            border-radius: 12px;
            border: 2px solid #D76D77;
            text-align: center;
            font-size: 18px;
            background: #f9f9f9;
        }
        button {
            width: 100%;
            padding: 15px;
            background: #3A1C71;
            color: white;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            font-size: 20px;
            font-weight: bold;
            transition: 0.3s;
        }
        button:hover {
            background: #D76D77;
        }
        .form-container {
            display: none;
            width: 100%;
            height: 100vh;
        }
        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }
    </style>
    <script>
        const accessCodes = {
            "16075": "https://forms.office.com/r/QBMJq48ECD",
            "70126": "https://forms.office.com/r/QBMJq48ECD",
            "86554": "https://forms.office.com/r/RM5FMb6q3y",
            "48261": "https://forms.office.com/r/RM5FMb6q3y",
            "2526": "https://forms.office.com/r/D87KEwa8Pg",
            "4545": "https://forms.office.com/r/UZaTGWQQKK"
        };
        
        function checkAccess() {
            let code = document.getElementById("codeInput").value;
            if (accessCodes[code]) {
                document.getElementById("loginContainer").style.display = "none";
                document.getElementById("formContainer").style.display = "block";
                document.getElementById("formEmbed").src = accessCodes[code];
            } else {
                alert("كود غير صحيح، الرجاء المحاولة مرة أخرى.");
            }
        }
    </script>
</head>
<body>
    <div id="loginContainer" class="container">
        <h1>تسجيل الدخول</h1>
        <input type="text" id="codeInput" placeholder="أدخل الكود الخاص بك">
        <button onclick="checkAccess()">دخول</button>
    </div>
    <div id="formContainer" class="form-container">
        <iframe id="formEmbed"></iframe>
    </div>

