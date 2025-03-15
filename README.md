
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mora</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            direction: rtl;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
        }
        h1 {
            color: #333;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>حاسبة الوقت</h1>
        <p id="currentDate"></p>
        <p id="currentTime"></p>
        <p id="daysRemaining"></p>
    </div>

    <script>
        function updateTime() {
            let now = new Date();
            let day = now.toLocaleDateString('ar-EG', { weekday: 'long' });
            let date = now.toLocaleDateString('ar-EG');
            let time = now.toLocaleTimeString('ar-EG');

            document.getElementById("currentDate").innerHTML = "اليوم: " + day + "، " + date;
            document.getElementById("currentTime").innerHTML = "الساعة الآن: " + time;

            // حساب الأيام المتبقية حتى 26 يونيو 2025
            let targetDate = new Date("2025-06-26");
            let timeDiff = targetDate - now;
            let daysRemaining = Math.ceil(timeDiff / (1000 * 60 * 60 * 24));

            document.getElementById("daysRemaining").innerHTML = "متبقي " + daysRemaining + " يوم حتى 26 يونيو 2025";
        }

        updateTime();
        setInterval(updateTime, 1000);
    </script>

