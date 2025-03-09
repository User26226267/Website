<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DF Time Info</title>
    <style>
        body {
            font-family: 'Fira Code', monospace;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
            text-align: center;
        }
        h1 {
            font-size: 48px;
            margin: 20px 0;
        }
        .container {
            padding: 20px;
        }
        .feature {
            margin: 20px 0;
            padding: 15px;
            border: 1px solid #ccc;
            border-radius: 10px;
            background-color: #fff;
        }
        .feature h2 {
            font-size: 24px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <h1>DF Time Info</h1>

    <div class="container">
        <!-- Current Date and Time -->
        <div class="feature" id="current-date-time">
            <h2>Current Date and Time</h2>
            <p id="date-time">Loading...</p>
        </div>

        <!-- World Clocks -->
        <div class="feature" id="world-clocks">
            <h2>World Clocks</h2>
            <div>
                <p>New York: <span id="new-york-time">Loading...</span></p>
                <p>London: <span id="london-time">Loading...</span></p>
                <p>Tokyo: <span id="tokyo-time">Loading...</span></p>
            </div>
        </div>

        <!-- Time Zone Converter -->
        <div class="feature" id="time-zone-converter">
            <h2>Time Zone Converter</h2>
            <p>Enter time to convert:</p>
            <input type="time" id="time-input" />
            <button onclick="convertTime()">Convert</button>
            <p id="conversion-result">Result will appear here.</p>
        </div>

        <!-- Countdown Timer -->
        <div class="feature" id="countdown-timer">
            <h2>Countdown Timer</h2>
            <p>Countdown to New Year's Day:</p>
            <p id="countdown">Loading...</p>
        </div>

        <!-- Sunrise and Sunset Tracker -->
        <div class="feature" id="sunrise-sunset">
            <h2>Sunrise and Sunset</h2>
            <p id="sunrise-sunset-info">Loading...</p>
        </div>

        <!-- Moon Phase -->
        <div class="feature" id="moon-phase">
            <h2>Moon Phase</h2>
            <p id="moon-phase-info">Loading...</p>
        </div>
    </div>

    <script>
        // Update Current Date and Time
        function updateDateTime() {
            const now = new Date();
            document.getElementById('date-time').textContent = now.toLocaleString();
        }
        setInterval(updateDateTime, 1000);

        // World Clocks
        function updateWorldClocks() {
            const now = new Date();
            const newYorkTime = new Date(now.toLocaleString("en-US", {timeZone: "America/New_York"}));
            const londonTime = new Date(now.toLocaleString("en-GB", {timeZone: "Europe/London"}));
            const tokyoTime = new Date(now.toLocaleString("en-JP", {timeZone: "Asia/Tokyo"}));
            document.getElementById('new-york-time').textContent = newYorkTime.toLocaleTimeString();
            document.getElementById('london-time').textContent = londonTime.toLocaleTimeString();
            document.getElementById('tokyo-time').textContent = tokyoTime.toLocaleTimeString();
        }
        setInterval(updateWorldClocks, 1000);

        // Time Zone Converter
        function convertTime() {
            const inputTime = document.getElementById('time-input').value;
            if (!inputTime) {
                document.getElementById('conversion-result').textContent = "Please enter a time.";
                return;
            }
            const [hours, minutes] = inputTime.split(':');
            const utcTime = new Date();
            utcTime.setUTCHours(hours, minutes);
            const localTime = utcTime.toLocaleTimeString();
            document.getElementById('conversion-result').textContent = `Converted Time: ${localTime}`;
        }

        // Countdown Timer
        function updateCountdown() {
            const now = new Date();
            const nextNewYear = new Date(now.getFullYear() + 1, 0, 1); // Jan 1 of next year
            const diff = nextNewYear - now;
            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);
            document.getElementById('countdown').textContent = `${days} days, ${hours} hours, ${minutes} minutes, ${seconds} seconds`;
        }
        setInterval(updateCountdown, 1000);

        // Sunrise and Sunset Tracker (Placeholder Implementation)
        document.getElementById('sunrise-sunset-info').textContent = "Sunrise: 7:00 AM, Sunset: 7:00 PM";

        // Moon Phase (Placeholder Implementation)
        document.getElementById('moon-phase-info').textContent = "Current Moon Phase: Waxing Gibbous";
    </script>
</body>
</html>
