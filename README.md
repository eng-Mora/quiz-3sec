<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة الطلاب</title>
    <style>
        body { 
            font-family: Arial, sans-serif; 
            text-align: center; 
            direction: rtl; 
            background-color: #f4f4f4; 
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }
        .container {
            width: 300px;
            padding: 20px;
            background: #0078D4;
            color: white;
            border-radius: 10px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
        }
        h1 {
            font-size: 24px;
        }
        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: none;
            text-align: center;
        }
        button {
            padding: 10px 20px;
            background: #005A9E;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background: #003E73;
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
