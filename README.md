# hitster-scan
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>Hitster Scan</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      background:#0f0f14;
      color:white;
      font-family:Arial, sans-serif;
      text-align:center;
      padding:30px;
    }
    button {
      font-size:20px;
      padding:14px 22px;
      border:none;
      border-radius:12px;
      background:#7b5cff;
      color:white;
    }
  </style>
</head>
<body>

<h1>🎶 Hitster Scan</h1>
<p>QR-Code scannen, um den Song zu hören</p>

<button onclick="scan()">📷 Scannen</button>

<script src="https://unpkg.com/html5-qrcode"></script>
<script>
function scan() {
  const scanner = new Html5Qrcode("reader");
  document.body.innerHTML += '<div id="reader"></div>';
  scanner.start(
    { facingMode: "environment" },
    { fps: 10, qrbox: 250 },
    (text) => {
      const id = new URL(text).searchParams.get("id");
      // später: Spotify-Link anhand der ID öffnen
      alert("Karte " + id + " gescannt");
      scanner.stop();
    }
  );
}
</script>

</body>
</html>
