<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Source Code Viewer</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #000;
      color: #0f0;
      text-align: center;
    }

    header {
      background: #0a0a0a;
      padding: 15px;
      font-size: 1.5em;
      font-weight: bold;
      color: #00ff80;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 15px #00ff80;
    }

    .container {
      margin: 40px auto;
      max-width: 800px;
      background: #111;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 0 25px #00ff80;
    }

    .input-box {
      width: 100%;
      padding: 12px;
      border-radius: 8px;
      border: none;
      margin-bottom: 15px;
      outline: none;
      background: #000;
      color: #0f0;
      font-size: 16px;
      box-shadow: 0 0 12px #00ff80 inset;
    }

    button {
      padding: 12px 24px;
      border: none;
      border-radius: 8px;
      background: #00ff80;
      color: #000;
      font-weight: bold;
      cursor: pointer;
      transition: 0.2s;
      box-shadow: 0 0 15px #00ff80;
    }

    button:hover {
      background: #0f0;
      box-shadow: 0 0 20px #0f0;
    }

    pre {
      background: #000;
      text-align: left;
      padding: 15px;
      border-radius: 10px;
      color: #0f0;
      max-height: 500px;
      overflow-y: auto;
      white-space: pre-wrap;
      word-wrap: break-word;
      box-shadow: 0 0 20px #00ff80 inset;
    }

    footer {
      margin-top: 30px;
      font-size: 14px;
    }

    a {
      color: #00ff80;
      text-decoration: none;
      font-weight: bold;
    }
  </style>
</head>
<body>

<header>Source Code Viewer</header>

<div class="container">
  <h2>👨‍💻 View Website Source Code</h2>
  <input type="text" id="urlInput" class="input-box" placeholder="Enter website URL (https://example.com)">
  <button onclick="viewSource()">🔍 View Source</button>
  <pre id="output">Enter a URL above and click "View Source"…</pre>
</div>

<footer>
  © Cyber Dev 2025 • <a href="#">Join our WhatsApp Channel</a>
</footer>

<script>
  async function viewSource() {
    const url = document.getElementById("urlInput").value.trim();
    const output = document.getElementById("output");

    if (!url) {
      output.textContent = "⚠️ Please enter a valid URL.";
      return;
    }

    try {
      output.textContent = "⏳ Fetching source code...";
      // Using a free proxy to bypass CORS
      const response = await fetch(`https://api.allorigins.win/get?url=${encodeURIComponent(url)}`);
      const data = await response.json();
      output.textContent = data.contents || "❌ Could not fetch source code.";
    } catch (err) {
      output.textContent = "❌ Error: " + err.message;
    }
  }
</script>

</body>
</html>
