<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Отдел поставок — Обновлённый интерфейс</title>

<!-- Внешние шрифты -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;500;700;800&display=swap" rel="stylesheet">

<style>
:root{
  --bg:#0b0b0c;
  --card:#0f1113;
  --muted:#a6b0b8;
  --accent1:#1d73c3;
  --accent2:#1d73c3;
  --glass: rgba(255,255,255,0.03);
  --glass-2: rgba(255,255,255,0.02);
  --radius:14px;
  --transition: 350ms cubic-bezier(.2,.9,.3,1);
}

*{box-sizing:border-box;margin:0;padding:0}
html,body,#app{height:100%}
body{
  background:
    radial-gradient(800px 500px at 10% 20%, rgba(29,115,195,0.06), transparent 8%),
    radial-gradient(700px 500px at 90% 80%, rgba(255,107,107,0.04), transparent 10%),
    var(--bg);
  color:#e9eef2;
  font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  line-height:1.4;
  padding:24px;
  position: relative;
  overflow-x: hidden;
}

/* Звездное небо */
.stars {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  pointer-events: none;
}

.star {
  position: absolute;
  background-color: white;
  border-radius: 50%;
  animation: twinkle var(--twinkle-duration, 4s) infinite ease-in-out;
  animation-delay: var(--twinkle-delay, 0s);
}

@keyframes twinkle {
  0%, 100% { opacity: 0.2; }
  50% { opacity: 1; }
}

/* Снегопад */
.snowflakes {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  pointer-events: none;
}

.snowflake {
  position: absolute;
  background-color: white;
  border-radius: 50%;
  animation: snowfall linear infinite;
}

@keyframes snowfall {
  0% { transform: translateY(-10px) rotate(0deg); }
  100% { transform: translateY(100vh) rotate(360deg); }
}

/* Конфетти */
.confetti {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  pointer-events: none;
}

.confetti-piece {
  position: absolute;
  width: 10px;
  height: 20px;
  animation: confetti-fall linear infinite;
}

@keyframes confetti-fall {
  0% { transform: translateY(-10px) rotate(0deg); }
  100% { transform: translateY(100vh) rotate(360deg); }
}

/* Хэллоуин */
.halloween {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  pointer-events: none;
}

.pumpkin {
  position: absolute;
  width: 30px;
  height: 30px;
  background: linear-gradient(45deg, #ff8c00, #ff4500);
  border-radius: 50% 50% 40% 40%;
  animation: float 8s ease-in-out infinite;
}

.pumpkin::before, .pumpkin::after {
  content: '';
  position: absolute;
  background: #000;
  border-radius: 50%;
}

.pumpkin::before {
  width: 8px;
  height: 8px;
  top: 8px;
  left: 6px;
}

.pumpkin::after {
  width: 8px;
  height: 8px;
  top: 8px;
  right: 6px;
}

.bat {
  position: absolute;
  color: #333;
  font-size: 20px;
  animation: fly 12s linear infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(5deg); }
}

@keyframes fly {
  0% { transform: translateX(-50px) translateY(0); }
  100% { transform: translateX(100vw) translateY(100px); }
}

/* Layout */
.container{
  max-width:1400px;
  margin:0 auto;
  display:grid;
  grid-template-columns: 320px 1fr;
  gap:24px;
  align-items:start;
  position: relative;
  z-index: 1;
}

/* Sidebar */
.sidebar{
  background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
  border:1px solid rgba(255,255,255,0.04);
  border-radius:var(--radius);
  padding:20px;
  position:relative;
  overflow:hidden;
  box-shadow: 0 6px 30px rgba(2,6,23,0.6);
  backdrop-filter: blur(6px);
  min-height:400px;
}

/* Logo / Title */
.brand{
  display:flex;
  align-items:center;
  gap:12px;
  margin-bottom:18px;
}
.logo{
  width:48px;height:48px;border-radius:10px;
  background:linear-gradient(135deg,var(--accent2),var(--accent1));
  display:flex;align-items:center;justify-content:center;font-weight:800;
  color:#05060a;font-size:18px;box-shadow: 0 6px 20px rgba(29,115,195,0.12);
}
.brand h2{font-size:18px;font-weight:700;color:#fff;letter-spacing:-0.2px}

/* Nav / quick stats */
.nav{
  display:flex;flex-direction:column;gap:12px;margin-bottom:18px;
}
.nav .nav-item{
  display:flex;align-items:center;justify-content:space-between;
  padding:10px 12px;border-radius:10px;cursor:pointer;
  transition:var(--transition);
  border:1px solid transparent;
  background: linear-gradient(180deg, transparent, rgba(255,255,255,0.01));
}
.nav .nav-item:hover{transform:translateY(-4px);border-color:rgba(255,255,255,0.03)}
.nav .nav-item .left{display:flex;gap:10px;align-items:center}
.kv{width:42px;height:42px;border-radius:8px;background:var(--glass);display:flex;align-items:center;justify-content:center;font-weight:700}
.kv.small{width:36px;height:36px}

/* Sidebar footer */
.sidebar .credits{
  margin-top:18px;padding-top:14px;border-top:1px solid rgba(255,255,255,0.03);
  color:var(--muted);font-size:13px;line-height:1.3;
}

/* Main content */
.main{
  min-height:600px;
  display:flex;flex-direction:column;gap:20px;
}

/* Top header */
.header{
  display:flex;align-items:center;justify-content:space-between;
  gap:16px;padding:20px;border-radius:var(--radius);
  background: linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.02));
  border:1px solid rgba(255,255,255,0.03);
  box-shadow: 0 6px 30px rgba(2,6,23,0.45);
}
.header .title{font-size:22px;font-weight:800}
.header .subtitle{color:var(--muted);font-weight:500}

/* Кнопка авторизации */
.auth-button {
  background: linear-gradient(135deg, var(--accent1), var(--accent2));
  border: none;
  border-radius: 20px;
  padding: 8px 16px;
  color: #04111a;
  font-weight: 600;
  font-size: 13px;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(29,115,195,0.2);
  display: flex;
  align-items: center;
  gap: 6px;
}

.auth-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(29,115,195,0.3);
}

.auth-button:active {
  transform: translateY(0);
}

.auth-button.authenticated {
  background: linear-gradient(135deg, #10b981, #059669);
}

.user-info {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
}

.user-avatar {
  width: 24px;
  height: 24px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea, #764ba2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  font-weight: bold;
}

/* Grid for cards */
.grid{
  display:grid;
  grid-template-columns: 1fr 360px;
  gap:20px;
}

/* Cards */
.card{
  background: linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));
  border:1px solid rgba(255,255,255,0.03);
  border-radius:12px;padding:18px;position:relative;overflow:hidden;
  transition: transform var(--transition), box-shadow var(--transition);
}
.card:hover{transform:translateY(-6px);box-shadow:0 20px 50px rgba(4,10,30,0.6)}

/* Mission / report list (left column in main card) */
.mission-list{display:flex;flex-direction:column;gap:12px}
.mission{
  display:flex;align-items:center;justify-content:space-between;padding:12px;border-radius:10px;
  background: linear-gradient(90deg, rgba(255,255,255,0.01), rgba(255,255,255,0.008));
  border:1px solid rgba(255,255,255,0.02);
  transition:var(--transition);
}
.mission:hover{transform:translateY(-4px)}
.mission .left{display:flex;gap:12px;align-items:center}
.mission .badge{
  min-width:56px;padding:8px 10px;border-radius:8px;text-align:center;font-weight:700;
  background:linear-gradient(135deg,var(--accent1),var(--accent2));color:#04111a;
  box-shadow:0 8px 22px rgba(29,115,195,0.08)
}

/* Progress */
.progress{
  height:12px;background:rgba(255,255,255,0.03);border-radius:999px;overflow:hidden;border:1px solid rgba(255,255,255,0.02)
}
.progress > i{
  display:block;height:100%;width:0%;border-radius:999px;background:linear-gradient(90deg,var(--accent2),var(--accent1));
  transition:width 1.6s cubic-bezier(.2,.9,.3,1);
  position:relative;
}
.progress > i::after{
  content:'';position:absolute;top:0;left:0;height:100%;width:30%;background:linear-gradient(90deg, transparent, rgba(255,255,255,0.12), transparent);
  animation: shimmer 2s linear infinite;
}
@keyframes shimmer{0%{transform:translateX(-120%)}100%{transform:translateX(120%)}}

/* Right column (stats) */
.stats-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
.stat{
  padding:12px;border-radius:10px;background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);
  text-align:center;border:1px solid rgba(255,255,255,0.02);
}
.stat .num{font-weight:800;font-size:18px}
.stat .lbl{color:var(--muted);font-size:13px}

/* Footer controls */
.footer-actions{display:flex;gap:12px;align-items:center;flex-wrap:wrap}
.button{
  padding:12px 18px;border-radius:999px;border:none;cursor:pointer;font-weight:700;
  transition: transform var(--transition), box-shadow var(--transition);
}
.button.primary{
  background:linear-gradient(135deg,var(--accent1),var(--accent2));color:#04111a;
  box-shadow:0 12px 30px rgba(29,115,195,0.12)
}
.button.ghost{
  background:transparent;border:1px solid rgba(255,255,255,0.03);color:var(--muted)
}
.button:active{transform:translateY(1px)}

/* Tiny helpers & responsive */
.small{font-size:13px;color:var(--muted)}
.center{display:flex;align-items:center;gap:8px}
.right{margin-left:auto}

/* Form styles */
.form-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-top: 16px;
}

.form-grid > div {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.form-grid > div:last-child {
  grid-column: span 2;
}

input, select, textarea {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 8px;
  padding: 10px 12px;
  color: #e9eef2;
  font-family: inherit;
  font-size: 14px;
  transition: border-color 0.2s ease;
}

input:focus, select:focus, textarea:focus {
  outline: none;
  border-color: var(--accent1);
}

.btn {
  padding: 10px 16px;
  border-radius: 8px;
  border: none;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
  font-family: inherit;
}

.btn-primary {
  background: linear-gradient(135deg, var(--accent1), var(--accent2));
  color: #04111a;
}

.btn-ghost {
  background: transparent;
  border: 1px solid rgba(255,255,255,0.06);
  color: var(--muted);
}

.muted {
  color: var(--muted);
}

/* Profile section styles */
.profile-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-top: 16px;
}

.profile-info {
  background: rgba(255,255,255,0.02);
  border-radius: 10px;
  padding: 16px;
  border: 1px solid rgba(255,255,255,0.03);
}

.profile-field {
  display: flex;
  justify-content: space-between;
  padding: 8px 0;
  border-bottom: 1px solid rgba(255,255,255,0.03);
}

.profile-field:last-child {
  border-bottom: none;
}

.profile-label {
  font-weight: 600;
  color: var(--muted);
}

.profile-value {
  font-weight: 500;
}

/* Стили для поля пароля в профиле */
.password-field {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 0;
  border-bottom: 1px solid rgba(255,255,255,0.03);
}

.password-field:last-child {
  border-bottom: none;
}

.password-label {
  font-weight: 600;
  color: var(--muted);
}

.password-value {
  font-weight: 500;
  font-family: monospace;
  letter-spacing: 1px;
}

.password-actions {
  display: flex;
  gap: 8px;
  margin-left: 12px;
}

.password-btn {
  background: transparent;
  border: 1px solid rgba(255,255,255,0.1);
  color: var(--muted);
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 11px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.password-btn:hover {
  background: rgba(255,255,255,0.05);
  color: #e9eef2;
}

.password-input {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 6px;
  padding: 6px 8px;
  color: #e9eef2;
  font-family: monospace;
  font-size: 13px;
  width: 150px;
  letter-spacing: 1px;
}

/* Стили для аватарок с различными рамками */
.profile-avatar-large {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea, #764ba2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 32px;
  font-weight: bold;
  margin: 0 auto 16px;
  position: relative;
  overflow: hidden;
  border: 3px solid rgba(255,255,255,0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.profile-avatar-large:hover {
  transform: scale(1.05);
}

.profile-avatar-large img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}

/* Стили различных рамок */
.avatar-frame-default {
  border: 3px solid rgba(255,255,255,0.1);
}

.avatar-frame-gold {
  border: 4px solid #FFD700;
  box-shadow: 0 0 15px rgba(255, 215, 0, 0.5);
}

.avatar-frame-silver {
  border: 4px solid #C0C0C0;
  box-shadow: 0 0 15px rgba(192, 192, 192, 0.5);
}

.avatar-frame-bronze {
  border: 4px solid #CD7F32;
  box-shadow: 0 0 15px rgba(205, 127, 50, 0.5);
}

.avatar-frame-gradient {
  border: 4px solid transparent;
  background: linear-gradient(135deg, var(--accent1), var(--accent2)) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
}

.avatar-frame-dotted {
  border: 4px dotted var(--accent1);
}

.avatar-frame-dashed {
  border: 4px dashed var(--accent2);
}

.avatar-frame-double {
  border: 6px double var(--accent1);
}

.avatar-frame-groove {
  border: 6px groove var(--accent1);
}

.avatar-frame-ridge {
  border: 6px ridge var(--accent2);
}

.avatar-frame-inset {
  border: 6px inset var(--accent1);
}

.avatar-frame-outset {
  border: 6px outset var(--accent2);
}

.avatar-frame-neon {
  border: 3px solid var(--accent1);
  box-shadow: 0 0 10px var(--accent1), 0 0 20px var(--accent1), 0 0 30px var(--accent1);
  animation: neon-pulse 2s infinite alternate;
}

@keyframes neon-pulse {
  from {
    box-shadow: 0 0 10px var(--accent1), 0 0 20px var(--accent1), 0 0 30px var(--accent1);
  }
  to {
    box-shadow: 0 0 15px var(--accent1), 0 0 25px var(--accent1), 0 0 35px var(--accent1);
  }
}

.avatar-frame-rainbow {
  border: 4px solid transparent;
  background: linear-gradient(45deg, #ff0000, #ff9900, #ffff00, #00ff00, #00ffff, #0000ff, #9900ff) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  animation: rainbow-rotate 3s linear infinite;
}

@keyframes rainbow-rotate {
  from {
    filter: hue-rotate(0deg);
  }
  to {
    filter: hue-rotate(360deg);
  }
}

.avatar-frame-crystal {
  border: 3px solid rgba(255,255,255,0.5);
  box-shadow: 
    0 0 10px rgba(255,255,255,0.3),
    inset 0 0 10px rgba(255,255,255,0.2);
  position: relative;
}

.avatar-frame-crystal::before {
  content: '';
  position: absolute;
  top: -3px;
  left: -3px;
  right: -3px;
  bottom: -3px;
  border-radius: 50%;
  background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
  animation: crystal-shine 3s linear infinite;
}

@keyframes crystal-shine {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.avatar-frame-fire {
  border: 3px solid transparent;
  background: linear-gradient(45deg, #ff0000, #ff9900, #ffff00) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  animation: fire-flicker 1s infinite alternate;
}

@keyframes fire-flicker {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.8;
  }
}

.avatar-frame-ice {
  border: 3px solid transparent;
  background: linear-gradient(45deg, #00ffff, #0066ff, #00ffff) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  animation: ice-glow 2s infinite alternate;
}

@keyframes ice-glow {
  from {
    filter: brightness(1);
  }
  to {
    filter: brightness(1.3);
  }
}

.avatar-upload {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0,0,0,0.7);
  color: white;
  padding: 8px;
  text-align: center;
  font-size: 12px;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.profile-avatar-large:hover .avatar-upload {
  opacity: 1;
}

.avatar-actions {
  display: flex;
  gap: 8px;
  justify-content: center;
  margin-top: 12px;
}

.avatar-btn {
  padding: 6px 12px;
  border-radius: 6px;
  border: none;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.avatar-btn.primary {
  background: linear-gradient(135deg, var(--accent1), var(--accent2));
  color: #04111a;
}

.avatar-btn.ghost {
  background: transparent;
  border: 1px solid rgba(255,255,255,0.1);
  color: var(--muted);
}

.avatar-btn:hover {
  transform: translateY(-1px);
}

/* Стили для выбора рамок */
.frame-selection {
  margin-top: 16px;
  padding: 16px;
  background: rgba(255,255,255,0.02);
  border-radius: 10px;
  border: 1px solid rgba(255,255,255,0.03);
}

.frame-selection h4 {
  margin-bottom: 12px;
  font-size: 14px;
  color: var(--muted);
}

.frame-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
  gap: 10px;
  margin-top: 8px;
}

.frame-option {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  font-weight: bold;
  position: relative;
  overflow: hidden;
}

.frame-option:hover {
  transform: scale(1.1);
}

.frame-option.active {
  transform: scale(1.1);
  box-shadow: 0 0 0 2px var(--accent1);
}

.frame-option.active::after {
  content: '✓';
  position: absolute;
  top: -5px;
  right: -5px;
  background: var(--accent1);
  color: white;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
}

/* Стили для выбора фона */
.background-selection {
  margin-top: 16px;
  padding: 16px;
  background: rgba(255,255,255,0.02);
  border-radius: 10px;
  border: 1px solid rgba(255,255,255,0.03);
}

.background-selection h4 {
  margin-bottom: 12px;
  font-size: 14px;
  color: var(--muted);
}

.background-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
  gap: 12px;
  margin-top: 8px;
}

.background-option {
  width: 80px;
  height: 60px;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  font-weight: bold;
  position: relative;
  overflow: hidden;
  border: 2px solid transparent;
  background: rgba(255,255,255,0.05);
  text-align: center;
  padding: 8px 4px;
}

.background-option:hover {
  transform: scale(1.05);
  border-color: rgba(255,255,255,0.1);
}

.background-option.active {
  transform: scale(1.05);
  border-color: var(--accent1);
  box-shadow: 0 0 0 2px var(--accent1);
}

.background-option.active::after {
  content: '✓';
  position: absolute;
  top: -8px;
  right: -8px;
  background: var(--accent1);
  color: white;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  z-index: 2;
}

.background-preview {
  width: 100%;
  height: 30px;
  border-radius: 4px;
  margin-bottom: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
}

/* Демо-аватар для предпросмотра рамок */
.frame-demo {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea, #764ba2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
}

/* Achievements */
.achievement {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px;
  border-radius: 10px;
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(255,255,255,0.03);
  transition: all 0.3s ease;
  width: 100%;
}

.achievement:hover {
  transform: translateY(-2px);
  border-color: rgba(255,255,255,0.1);
}

.achievement.locked {
  opacity: 0.4;
  filter: grayscale(1);
}

.achievement-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
  background: linear-gradient(135deg, var(--accent1), var(--accent2));
  box-shadow: 0 4px 12px rgba(29,115,195,0.2);
  flex-shrink: 0;
}

.achievement.locked .achievement-icon {
  background: rgba(255,255,255,0.05);
  box-shadow: none;
}

.achievement-content {
  flex: 1;
  min-width: 0;
}

.achievement-name {
  font-weight: 600;
  font-size: 13px;
  line-height: 1.2;
  margin-bottom: 4px;
}

.achievement-desc {
  font-size: 11px;
  color: var(--muted);
  line-height: 1.2;
}

.achievement-progress {
  width: 100%;
  height: 4px;
  background: rgba(255,255,255,0.05);
  border-radius: 2px;
  overflow: hidden;
  margin-top: 6px;
}

.achievement-progress-bar {
  height: 100%;
  background: linear-gradient(90deg, var(--accent1), var(--accent2));
  transition: width 0.5s ease;
}

.achievements-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 12px;
  max-height: 400px;
  overflow-y: auto;
}

.achievements-list::-webkit-scrollbar {
  width: 4px;
}

.achievements-list::-webkit-scrollbar-track {
  background: rgba(255,255,255,0.02);
  border-radius: 2px;
}

.achievements-list::-webkit-scrollbar-thumb {
  background: var(--accent1);
  border-radius: 2px;
}

.achievements-stats {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
  padding: 8px 0;
  border-bottom: 1px solid rgba(255,255,255,0.03);
}

.achievements-count {
  font-weight: 700;
  font-size: 14px;
}

.achievements-progress {
  font-size: 12px;
  color: var(--muted);
}

/* Login Modal */
.login-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(11, 11, 12, 0.8);
  backdrop-filter: blur(8px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.login-modal.active {
  opacity: 1;
  visibility: visible;
}

.login-content {
  background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
  border: 1px solid rgba(255,255,255,0.04);
  border-radius: var(--radius);
  padding: 30px;
  width: 100%;
  max-width: 400px;
  box-shadow: 0 20px 60px rgba(2,6,23,0.8);
  transform: translateY(20px);
  transition: transform 0.3s ease;
}

.login-modal.active .login-content {
  transform: translateY(0);
}

.login-header {
  text-align: center;
  margin-bottom: 24px;
}

.login-header h3 {
  font-size: 24px;
  font-weight: 800;
  margin-bottom: 8px;
}

.login-form {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.form-group label {
  font-weight: 600;
  color: var(--muted);
  font-size: 14px;
}

.login-actions {
  display: flex;
  gap: 12px;
  margin-top: 8px;
}

.login-actions .btn {
  flex: 1;
}

.remember-me {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
}

.remember-me input[type="checkbox"] {
  width: 16px;
  height: 16px;
}

.remember-me label {
  font-size: 14px;
  color: var(--muted);
  cursor: pointer;
}

.close-modal {
  position: absolute;
  top: 16px;
  right: 16px;
  background: transparent;
  border: none;
  color: var(--muted);
  font-size: 20px;
  cursor: pointer;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}

.close-modal:hover {
  background: rgba(255,255,255,0.05);
  color: #e9eef2;
}

/* Auth Tabs */
.auth-tabs {
  display: flex;
  margin-bottom: 24px;
  border-bottom: 1px solid rgba(255,255,255,0.1);
}

.auth-tab {
  flex: 1;
  text-align: center;
  padding: 12px;
  cursor: pointer;
  border-bottom: 2px solid transparent;
  transition: all 0.3s ease;
}

.auth-tab.active {
  border-bottom: 2px solid var(--accent1);
  color: var(--accent1);
}

.auth-tab:hover {
  background: rgba(255,255,255,0.05);
}

/* Стили для админ-панели */
.admin-section {
  margin-bottom: 24px;
  padding: 16px;
  background: rgba(255,255,255,0.02);
  border-radius: 10px;
  border: 1px solid rgba(255,255,255,0.03);
}

.admin-section h3 {
  margin-bottom: 16px;
  font-size: 18px;
  color: #fff;
}

.admin-tabs {
  display: flex;
  border-bottom: 1px solid rgba(255,255,255,0.1);
  margin-bottom: 16px;
}

.admin-tab {
  padding: 12px 16px;
  cursor: pointer;
  border-bottom: 2px solid transparent;
  transition: all 0.3s ease;
  font-weight: 600;
}

.admin-tab.active {
  border-bottom: 2px solid var(--accent1);
  color: var(--accent1);
}

.admin-tab:hover {
  background: rgba(255,255,255,0.05);
}

.admin-content {
  display: none;
}

.admin-content.active {
  display: block;
}

/* Таблицы */
.admin-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 12px;
}

.admin-table th,
.admin-table td {
  padding: 12px;
  text-align: left;
  border-bottom: 1px solid rgba(255,255,255,0.03);
}

.admin-table th {
  font-weight: 600;
  color: var(--muted);
  font-size: 14px;
}

.admin-table tr:hover {
  background: rgba(255,255,255,0.02);
}

.status-badge {
  padding: 4px 8px;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
}

.status-pending {
  background: rgba(255,193,7,0.1);
  color: #ffc107;
}

.status-approved {
  background: rgba(40,167,69,0.1);
  color: #28a745;
}

.status-rejected {
  background: rgba(220,53,69,0.1);
  color: #dc3545;
}

/* Графики */
.chart-container {
  background: rgba(255,255,255,0.02);
  border-radius: 10px;
  padding: 16px;
  margin-top: 16px;
  height: 300px;
  position: relative;
}

.chart-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--muted);
  font-size: 14px;
}

/* Фильтры и поиск */
.admin-filters {
  display: flex;
  gap: 12px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

.admin-search {
  flex: 1;
  min-width: 200px;
}

.admin-search input {
  width: 100%;
}

.filter-group {
  display: flex;
  gap: 8px;
}

/* Действия */
.admin-actions {
  display: flex;
  gap: 8px;
  margin-top: 16px;
}

.action-btn {
  padding: 8px 12px;
  border-radius: 6px;
  border: none;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.action-btn.approve {
  background: rgba(40,167,69,0.1);
  color: #28a745;
  border: 1px solid rgba(40,167,69,0.3);
}

.action-btn.reject {
  background: rgba(220,53,69,0.1);
  color: #dc3545;
  border: 1px solid rgba(220,53,69,0.3);
}

.action-btn.edit {
  background: rgba(23,162,184,0.1);
  color: #17a2b8;
  border: 1px solid rgba(23,162,184,0.3);
}

.action-btn.delete {
  background: rgba(108,117,125,0.1);
  color: #6c757d;
  border: 1px solid rgba(108,117,125,0.3);
}

.action-btn:hover {
  transform: translateY(-1px);
  opacity: 0.9;
}

/* Статистика */
.stats-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 16px;
  margin-bottom: 24px;
}

.stat-card {
  background: rgba(255,255,255,0.02);
  border-radius: 10px;
  padding: 16px;
  border: 1px solid rgba(255,255,255,0.03);
  text-align: center;
}

.stat-number {
  font-size: 24px;
  font-weight: 800;
  margin-bottom: 8px;
}

.stat-label {
  color: var(--muted);
  font-size: 14px;
}

/* Роли пользователей */
.role-badge {
  padding: 4px 8px;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
}

.role-admin {
  background: rgba(220,53,69,0.1);
  color: #dc3545;
}

.role-moderator {
  background: rgba(255,193,7,0.1);
  color: #ffc107;
}

.role-user {
  background: rgba(40,167,69,0.1);
  color: #28a745;
}

.role-guest {
  background: rgba(108,117,125,0.1);
  color: #6c757d;
}

/* Модальные окна */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(11, 11, 12, 0.8);
  backdrop-filter: blur(8px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.modal.active {
  opacity: 1;
  visibility: visible;
}

.modal-content {
  background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
  border: 1px solid rgba(255,255,255,0.04);
  border-radius: var(--radius);
  padding: 30px;
  width: 100%;
  max-width: 600px;
  max-height: 80vh;
  overflow-y: auto;
  box-shadow: 0 20px 60px rgba(2,6,23,0.8);
  transform: translateY(20px);
  transition: transform 0.3s ease;
}

.modal.active .modal-content {
  transform: translateY(0);
}

.modal-header {
  display: flex;
  justify-content: between;
  align-items: center;
  margin-bottom: 20px;
}

.modal-header h3 {
  margin: 0;
  font-size: 20px;
}

.close-modal {
  background: transparent;
  border: none;
  color: var(--muted);
  font-size: 20px;
  cursor: pointer;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}

.close-modal:hover {
  background: rgba(255,255,255,0.05);
  color: #e9eef2;
}

/* Accessibility improvements */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

/* Focus styles */
button:focus-visible,
.nav-item:focus-visible {
  outline: 2px solid var(--accent1);
  outline-offset: 2px;
}

/* Fix for mission icon height */
.mission-icon {
  width:46px;
  height:46px;
  border-radius:10px;
  display:flex;
  align-items:center;
  justify-content:center;
  font-weight:800;
}

@media (max-width:1100px){
  .container{grid-template-columns:1fr; padding-bottom:60px}
  .grid{grid-template-columns:1fr}
  .stats-grid{grid-template-columns:repeat(2,1fr)}
  .profile-grid{grid-template-columns:1fr}
}

@media (max-width:768px){
  .profile-grid {
    grid-template-columns: 1fr;
  }
  
  .achievements-list {
    max-height: 300px;
  }
  
  .frame-grid {
    grid-template-columns: repeat(auto-fill, minmax(50px, 1fr));
  }
  
  .frame-option {
    width: 50px;
    height: 50px;
  }
  
  .background-grid {
    grid-template-columns: repeat(auto-fill, minmax(70px, 1fr));
  }
  
  .background-option {
    width: 70px;
    height: 55px;
  }
  
  .admin-tabs {
    flex-direction: column;
  }
  
  .admin-filters {
    flex-direction: column;
  }
  
  .admin-search {
    min-width: 100%;
  }
  
  .stats-cards {
    grid-template-columns: 1fr;
  }
  
  .admin-table {
    font-size: 12px;
  }
  
  .admin-table th,
  .admin-table td {
    padding: 8px 4px;
  }
}

@media (max-width:480px){
  .login-content {
    margin: 20px;
    padding: 20px;
  }
  
  .login-actions {
    flex-direction: column;
  }
  
  .profile-avatar-large {
    width: 100px;
    height: 100px;
    font-size: 24px;
  }
  
  .avatar-actions {
    flex-direction: column;
  }
  
  .achievement {
    padding: 8px;
  }
  
  .achievement-icon {
    width: 32px;
    height: 32px;
    font-size: 14px;
  }
  
  .frame-grid {
    grid-template-columns: repeat(auto-fill, minmax(45px, 1fr));
    gap: 8px;
  }
  
  .frame-option {
    width: 45px;
    height: 45px;
    font-size: 10px;
  }
  
  .background-grid {
    grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
    gap: 8px;
  }
  
  .background-option {
    width: 60px;
    height: 50px;
    font-size: 9px;
  }
  
  .modal-content {
    margin: 20px;
    padding: 20px;
  }
}
</style>
</head>
<body>
<!-- Звездное небо -->
<div class="stars" id="stars"></div>

<!-- Снегопад -->
<div class="snowflakes" id="snowflakes"></div>

<!-- Конфетти -->
<div class="confetti" id="confetti"></div>

<!-- Хэллоуин -->
<div class="halloween" id="halloween"></div>

<div id="app" class="app">
  <div class="container">

    <!-- SIDEBAR -->
    <aside class="sidebar" aria-label="Навигация отдела поставок">
      <div class="brand">
        <div class="logo" aria-hidden="true">🚚</div>
        <div>
          <h2>Отдел поставок</h2>
          <div class="small"> Личный сайт Отдела Поставок</div>
        </div>
      </div>

      <nav class="nav" aria-label="Пункты меню">
        <div class="nav-item" tabindex="0" role="button" onclick="showMainView()" onkeydown="handleKeyPress(event, 'main')">
          <div class="left"><div class="kv small" aria-hidden="true">🔮</div><div>
            <div style="font-weight:700">Главная</div>
            <div class="small">Главная страница</div>
          </div></div>
          <div class="small">→</div>
        </div>

        <div class="nav-item" tabindex="0" role="button" onclick="showProfileView()" onkeydown="handleKeyPress(event, 'profile')">
          <div class="left"><div class="kv small" aria-hidden="true">🎨</div><div>
            <div style="font-weight:700">Профиль</div>
            <div class="small">Ваш профиль который вы можете настроить</div>
          </div></div>
          <div class="small">→</div>
        </div>

        <div class="nav-item" tabindex="0" role="button" onclick="showCreateView()" onkeydown="handleKeyPress(event, 'create')">
          <div class="left"><div class="kv small" aria-hidden="true">📄</div><div>
            <div style="font-weight:700">Подача отчета</div>
            <div class="small">Подача еженедельного и отчета на повышение</div>
          </div></div>
          <div class="small">→</div>
        </div>

        <div class="nav-item" tabindex="0" role="button" onclick="showExamView()" onkeydown="handleKeyPress(event, 'exam')">
          <div class="left"><div class="kv small" aria-hidden="true">🎓</div><div>
            <div style="font-weight:700">Заяка на экзамен ОП</div>
            <div class="small">Заявка на прохождение стажировки</div>
          </div></div>
          <div class="small">→</div>
        </div>
        
        <div class="nav-item" tabindex="0" role="button" onclick="showAdminView()" onkeydown="handleKeyPress(event, 'admin')">
          <div class="left"><div class="kv small" aria-hidden="true">⚙️</div><div>
            <div style="font-weight:700">Админ панель</div>
            <div class="small">Управление системой</div>
          </div></div>
          <div class="small">→</div>
        </div>
      </nav>

      <div class="credits small">
        <div><strong>Разработано:</strong> Alexandr Sakurai. При Заведующим Отдела Поставок Sasha Sasik. </div>
        <div style="margin-top:8px">© 2025 EMS. Все права защищены.</div>
      </div>
    </aside>

    <!-- Login Modal -->
    <div class="login-modal" id="loginModal">
      <div class="login-content">
        <button class="close-modal" onclick="closeLoginModal()">×</button>
        <div class="login-header">
          <h3 id="authModalTitle">Вход в систему</h3>
          <div class="small muted" id="authModalSubtitle">Войдите в ваш аккаунт</div>
        </div>

        <div class="auth-tabs">
          <div class="auth-tab active" onclick="switchAuthTab('login')">Вход</div>
          <div class="auth-tab" onclick="switchAuthTab('register')">Регистрация</div>
        </div>

        <form class="login-form" id="loginForm">
          <div class="form-group" id="registerFields" style="display:none;">
            <label for="registerName">Полное имя</label>
            <input type="text" id="registerName" placeholder="Введите ваше имя">
          </div>

          <div class="form-group">
            <label for="authEmail">Email адрес</label>
            <input type="email" id="authEmail" placeholder="your@email.com">
          </div>

          <div class="form-group" id="nicknameField" style="display:none;">
            <label for="registerNickname">Никнейм</label>
            <input type="text" id="registerNickname" placeholder="Придумайте никнейм">
          </div>

          <div class="form-group">
            <label for="authPassword">Пароль</label>
            <input type="password" id="authPassword" placeholder="Введите пароль">
          </div>

          <div class="form-group" id="confirmPasswordField" style="display:none;">
            <label for="confirmPassword">Подтвердите пароль</label>
            <input type="password" id="confirmPassword" placeholder="Повторите пароль">
          </div>

          <div class="form-group" id="rememberMe" style="display:flex;align-items:center;gap:8px;">
            <input type="checkbox" id="rememberCheckbox">
            <label for="rememberCheckbox" class="small">Запомнить меня</label>
          </div>

          <div class="login-actions">
            <button type="submit" class="btn btn-primary" id="authSubmitBtn">Войти в систему</button>
            <button type="button" class="btn btn-ghost" onclick="closeLoginModal()">Отмена</button>
          </div>
        </form>
      </div>
    </div>

    <!-- Profile View -->
    <section id="profileView" style="display:none">
      <div class="profile-grid">
        <!-- Левая колонка - основная информация -->
        <div class="card">
          <h3>Профиль пользователя</h3>
          <div class="profile-info">
            <div class="profile-avatar-large avatar-frame-default" id="profileAvatar" onclick="document.getElementById('avatarInput').click()">
              <div class="avatar-upload">Нажмите для загрузки</div>
            </div>
            <div class="avatar-actions">
              <button class="avatar-btn primary" onclick="document.getElementById('avatarInput').click()">
                📷 Загрузить аватар
              </button>
              <button class="avatar-btn ghost" onclick="removeAvatar()">
                🗑️ Удалить
              </button>
            </div>
            <input type="file" id="avatarInput" accept="image/*" style="display:none" onchange="handleAvatarUpload(event)" />
            
            <!-- Новое поле для пароля -->
            <div class="password-field">
              <span class="password-label">Пароль:</span>
              <div style="display: flex; align-items: center;">
                <span class="password-value" id="profilePassword">••••••••</span>
                <div class="password-actions">
                  <button class="password-btn" onclick="togglePasswordVisibility()" id="togglePasswordBtn">
                    👁️ Показать
                  </button>
                  <button class="password-btn" onclick="changePassword()">
                    ✏️ Изменить
                  </button>
                </div>
              </div>
            </div>
            
            <div class="profile-field">
              <span class="profile-label">Имя:</span>
              <span class="profile-value" id="profileName">Не авторизован</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Email:</span>
              <span class="profile-value" id="profileEmail">-</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Никнейм:</span>
              <span class="profile-value" id="profileNickname">-</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">ID профиля:</span>
              <span class="profile-value" id="profileId">-</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Статус:</span>
              <span class="profile-value" id="profileStatus">Не авторизован</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Роль:</span>
              <span class="profile-value" id="profileRole">Гость</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Дата регистрации:</span>
              <span class="profile-value" id="profileRegDate">-</span>
            </div>
          </div>
          
          <!-- Выбор рамки для аватара -->
          <div class="frame-selection">
            <h4>Выберите рамку для аватара:</h4>
            <div class="frame-grid" id="frameSelection">
              <!-- Рамки будут добавлены через JavaScript -->
            </div>
          </div>
          
          <!-- Выбор фона -->
          <div class="background-selection">
            <h4>Выберите фон:</h4>
            <div class="background-grid" id="backgroundSelection">
              <!-- Фоны будут добавлены через JavaScript -->
            </div>
          </div>
          
          <div style="display:flex;gap:8px;margin-top:16px">
            <button class="btn btn-primary" onclick="handleAuth()" id="profileAuthBtn">Войти в систему</button>
            <button class="btn btn-ghost" onclick="showMainView()">Вернуться на главную</button>
          </div>
        </div>

        <!-- Правая колонка - достижения и статистика активности -->
        <div class="card">
          <h3>Достижения</h3>
          <div class="achievements-stats">
            <div class="achievements-count" id="achievementsCount">0/10</div>
            <div class="achievements-progress" id="achievementsProgress">0%</div>
          </div>
          <div id="achList" class="achievements-list"></div>
          
          <!-- Статистика активности (перемещена под достижения) -->
          <div class="profile-info" style="margin-top: 20px;">
            <h4 style="margin-bottom:16px">Статистика активности</h4>
            <div class="profile-field">
              <span class="profile-label">Отправлено отчетов:</span>
              <span class="profile-value" id="profileReportsCount">0</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Последняя активность:</span>
              <span class="profile-value" id="profileLastActivity">-</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Рейтинг:</span>
              <span class="profile-value" id="profileRating">-</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Размер аватара:</span>
              <span class="profile-value" id="avatarSize">-</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Текущая рамка:</span>
              <span class="profile-value" id="currentFrame">По умолчанию</span>
            </div>
            <div class="profile-field">
              <span class="profile-label">Текущий фон:</span>
              <span class="profile-value" id="currentBackground">Звездное небо</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Create -->
    <section id="createView" style="display:none">
      <div class="card">
        <h3>Новый отчёт</h3>
        <div class="form-grid" style="margin-top:10px">
          <div>
            <label class="small muted">Название</label>
            <input id="titleInput" type="text" placeholder="Краткое название" />
          </div>
          <div>
            <label class="small muted">Тип</label>
            <select id="typeInput">
              <option value="promotion">На повышение</option>
              <option value="weekly">Еженедельный</option>
            </select>
          </div>

          <div style="grid-column:span 2">
            <label class="small muted">Описание</label>
            <textarea id="descInput" placeholder="Подробности..."></textarea>
          </div>

          <div>
            <label class="small muted">Баллы (общие) — автоподсчёт для недельного</label>
            <input id="pointsInput" type="number" min="0" placeholder="0" />
          </div>
        </div>

        <!-- Weekly specific fields (hidden unless type == weekly) -->
        <div id="weeklyFields" style="margin-top:12px;display:none">
          <h4 class="small muted">Еженедельный рапорт</h4>
          <div style="display:grid;grid-template-columns:repeat(2,1fr);gap:8px;margin-top:8px">
            <div>
              <label class="small muted">Ваше Имя Фамилия *</label>
              <input id="weekly_name" type="text" placeholder="Иван Иванов" />
            </div>
            <div>
              <label class="small muted">Начало недели *</label>
              <input id="weekly_start" type="date" />
            </div>
            <div>
              <label class="small muted">Конец недели *</label>
              <input id="weekly_end" type="date" />
            </div>
            <div>
              <label class="small muted">Был ли у Вас отпуск на неделе?</label>
              <div style="display:flex;gap:8px;margin-top:6px"><label><input type="radio" name="weekly_vac" value="no" checked/> Нет</label> <label style="margin-left:8px"><input type="radio" name="weekly_vac" value="yes"/> Да</label></div>
            </div>

            <!-- Metrics rows -->
            <div style="grid-column:span 2;margin-top:6px;border-top:1px dashed rgba(255,255,255,0.03);padding-top:8px">
              <div class="small muted">Поля (впишите Количество, затем Балл за единицу — система умножит)</div>
              <div style="display:grid;grid-template-columns:2fr 1fr 1fr;gap:8px;margin-top:8px;font-size:13px">
                <div><strong>Пункт</strong></div><div><strong>Кол-во</strong></div><div><strong>Баллы/ед.</strong></div>

                <div>Участие в поставке EMS</div><input id="m_supply_qty" type="number" value="0" min="0" /><input id="m_supply_pts" type="number" value="0" min="0" />

                <div>Реанимация</div><input id="m_reanim_qty" type="number" value="0" min="0" /><input id="m_reanim_pts" type="number" value="0" min="0" />

                <div>Проведение осмотра</div><input id="m_exam_qty" type="number" value="0" min="0" /><input id="m_exam_pts" type="number" value="0" min="0" />

                <div>Укол от наркозависимости</div><input id="m_inj_qty" type="number" value="0" min="0" /><input id="m_inj_pts" type="number" value="0" min="0" />

                <div>Участие в МП/ГМП</div><input id="m_mp_qty" type="number" value="0" min="0" /><input id="m_mp_pts" type="number" value="0" min="0" />

                <div>Дежурство LS дневное/ночное (часов)</div><input id="m_shift_qty" type="number" value="0" min="0" /><input id="m_shift_pts" type="number" value="0" min="0" />

                <div>Отправить рапорт (СО)</div><input id="m_report_qty" type="number" value="0" min="0" /><input id="m_report_pts" type="number" value="0" min="0" />

                <div>Выезд на СО</div><input id="m_dispatch_qty" type="number" value="0" min="0" /><input id="m_dispatch_pts" type="number" value="0" min="0" />

                <div>Отправить вторичный рапорт на нарушение</div><input id="m_secondary_qty" type="number" value="0" min="0" /><input id="m_secondary_pts" type="number" value="0" min="0" />

                <div>Дополнительные Баллы (сумма)</div><input id="m_extra_qty" type="number" value="0" min="0" /><input id="m_extra_pts" type="number" value="1" min="0" />
              </div>
            </div>

            <div style="grid-column:span 2;margin-top:10px;display:flex;gap:8px;align-items:center">
              <div style="flex:1"><label class="small muted">Общее кол-во баллов *</label><input id="weekly_total" type="number" value="0" /></div>
              <div><button class="btn btn-ghost" id="calcWeekly">Посчитать</button></div>
              <div><button class="btn btn-ghost" id="fillFromTemplate">Заполнить шаблон</button></div>
            </div>

          </div>
        </div>

        <!-- Promotion specific fields (hidden unless type == promotion) -->
        <div id="promotionFields" style="margin-top:12px;display:none">
          <h4 class="small muted">Отчет на повышение</h4>
          <div style="display:grid;grid-template-columns:1fr;gap:12px;margin-top:8px">
            <div>
              <label class="small muted">Ваше Имя Фамилия *</label>
              <input id="promotion_name" type="text" placeholder="Иван Иванов" />
            </div>
            
            <div>
              <label class="small muted">Текущая должность *</label>
              <select id="promotion_current_position">
                <option value="intern">Стажёр</option>
                <option value="paramedic">Фельдшер</option>
                <option value="senior_paramedic">Старший фельдшер</option>
                <option value="team_lead">Старший смены</option>
                <option value="deputy">Заместитель начальника ОП</option>
              </select>
            </div>
            
            <div>
              <label class="small muted">Желаемая должность *</label>
              <select id="promotion_desired_position">
                <option value="paramedic">Фельдшер</option>
                <option value="senior_paramedic">Старший фельдшер</option>
                <option value="team_lead">Старший смены</option>
                <option value="deputy">Заместитель начальника ОП</option>
                <option value="head">Начальник ОП</option>
              </select>
            </div>
            
            <div>
              <label class="small muted">Дата начала работы в текущей должности *</label>
              <input id="promotion_start_date" type="date" />
            </div>
            
            <div>
              <label class="small muted">Общий стаж работы в ОП (месяцев) *</label>
              <input id="promotion_experience" type="number" min="0" placeholder="6" />
            </div>
            
            <!-- Достижения и квалификации -->
            <div style="grid-column:span 1;margin-top:6px;border-top:1px dashed rgba(255,255,255,0.03);padding-top:8px">
              <div class="small muted">Достижения и дополнительная квалификация</div>
              <div style="display:grid;grid-template-columns:2fr 1fr;gap:8px;margin-top:8px;font-size:13px">
                <div><strong>Показатель</strong></div><div><strong>Количество</strong></div>

                <div>Участие в поставке EMS</div><input id="p_successful_deliveries" type="number" value="0" min="0" />

                <div>Реанимация</div><input id="p_trainings_conducted" type="number" value="0" min="0" />

                <div>Проведение осмотра</div><input id="p_mentorships" type="number" value="0" min="0" />

                <div>Укол от наркозависимости</div><input id="p_initiatives" type="number" value="0" min="0" />

                <div>Участие в МП/ГМП</div><input id="p_initiatives" type="number" value="0" min="0" />

                <div>Укол от наркозависимости</div><input id="p_initiatives" type="number" value="0" min="0" />

                <div>Дежурство LS дневное/ночное</div><input id="p_initiatives" type="number" value="0" min="0" />

                <div>Отправить рапорт (СО)</div><input id="p_initiatives" type="number" value="0" min="0" />

                <div>Выезд на СО</div><input id="p_initiatives" type="number" value="0" min="0" />

                <div>Отправить вторичный рапорт на нарушение</div><input id="p_initiatives" type="number" value="0" min="0" />

            <!-- Обоснование повышения -->
            <div style="grid-column:span 1;margin-top:10px">
              <label class="small muted">Доп. Баллы *</label>
              <textarea id="promotion_justification" placeholder="Доп. Баллы" rows="4"></textarea>
            </div>

          </div>
        </div>

        <div style="display:flex;gap:8px;margin-top:12px">
          <button class="btn btn-primary" id="submitReport">Сохранить</button>
          <button class="btn btn-ghost" id="clearForm">Очистить</button>
          <div class="right small muted" id="formStatus">готов</div>
        </div>
      </div>
    </section>

    <!-- Exam Application -->
     <section id="examView" style="display:none">
       <div class="card">
         <h3>Заявка на здачу экзамена ОП</h3>
         <div class="form-grid">
           <div>
             <label class="small muted">Имя фамилия</label>
             <input id="examNameInput" type="text" placeholder="Имя и фамилия" />
           </div>
           <div>
             <label class="small muted">Экзамен</label>
             <select id="examTypeInput"><option value="promotion">Экзамен</option></select>
           </div>
           <div style="grid-column:span 2">
             <label class="small muted">Время когда вам будет удобно</label>
             <textarea id="examTimeInput" placeholder="Время..."></textarea>
           </div>
           <div>
         <div style="display:flex;gap:8px;margin-top:12px">
           <button class="btn btn-primary" id="submitExam">Отправить</button>
           <button class="btn btn-ghost" id="clearExamForm">Очистить</button>
           <div class="right small muted" id="examFormStatus">готов</div>
        </div>
       </div>
     </section>

    <!-- Admin Panel -->
    <section id="adminView" style="display:none">
      <div class="card">
        <h2>Админ панель</h2>
        <div class="small muted" style="margin-bottom: 20px;">Управление системой, отчетами и пользователями</div>
        
        <!-- Статистика -->
        <div class="stats-cards">
          <div class="stat-card">
            <div class="stat-number" id="adminTotalReports">0</div>
            <div class="stat-label">Всего отчетов</div>
          </div>
          <div class="stat-card">
            <div class="stat-number" id="adminTotalUsers">0</div>
            <div class="stat-label">Пользователей</div>
          </div>
          <div class="stat-card">
            <div class="stat-number" id="adminPendingReports">0</div>
            <div class="stat-label">Ожидают проверки</div>
          </div>
          <div class="stat-card">
            <div class="stat-number" id="adminAvgPoints">0</div>
            <div class="stat-label">Средний балл</div>
          </div>
        </div>

        <!-- Вкладки админ-панели -->
        <div class="admin-tabs">
          <div class="admin-tab active" onclick="switchAdminTab('reports')">Отчеты</div>
          <div class="admin-tab" onclick="switchAdminTab('users')">Пользователи</div>
          <div class="admin-tab" onclick="switchAdminTab('statistics')">Статистика</div>
          <div class="admin-tab" onclick="switchAdminTab('settings')">Настройки</div>
        </div>

        <!-- Содержимое вкладок -->
        
        <!-- Вкладка отчетов -->
        <div class="admin-content active" id="adminReports">
          <div class="admin-filters">
            <div class="admin-search">
              <input type="text" id="reportSearch" placeholder="Поиск по отчетам..." onkeyup="filterReports()">
            </div>
            <div class="filter-group">
              <select id="reportTypeFilter" onchange="filterReports()">
                <option value="all">Все типы</option>
                <option value="weekly">Еженедельные</option>
                <option value="promotion">На повышение</option>
              </select>
              <select id="reportStatusFilter" onchange="filterReports()">
                <option value="all">Все статусы</option>
                <option value="pending">Ожидает</option>
                <option value="approved">Одобрено</option>
                <option value="rejected">Отклонено</option>
              </select>
            </div>
          </div>
          
          <div class="admin-table-container" style="max-height: 400px; overflow-y: auto;">
            <table class="admin-table" id="reportsTable">
              <thead>
                <tr>
                  <th>ID</th>
                  <th>Название</th>
                  <th>Автор</th>
                  <th>Тип</th>
                  <th>Дата</th>
                  <th>Баллы</th>
                  <th>Статус</th>
                  <th>Действия</th>
                </tr>
              </thead>
              <tbody id="reportsTableBody">
                <!-- Отчеты будут загружены через JavaScript -->
              </tbody>
            </table>
          </div>
        </div>

        <!-- Вкладка пользователей -->
        <div class="admin-content" id="adminUsers">
          <div class="admin-filters">
            <div class="admin-search">
              <input type="text" id="userSearch" placeholder="Поиск пользователей..." onkeyup="filterUsers()">
            </div>
            <div class="filter-group">
              <select id="userRoleFilter" onchange="filterUsers()">
                <option value="all">Все роли</option>
                <option value="admin">Администратор</option>
                <option value="moderator">Модератор</option>
                <option value="user">Пользователь</option>
                <option value="guest">Гость</option>
              </select>
            </div>
          </div>
          
          <div class="admin-table-container" style="max-height: 400px; overflow-y: auto;">
            <table class="admin-table" id="usersTable">
              <thead>
                <tr>
                  <th>ID</th>
                  <th>Имя</th>
                  <th>Email</th>
                  <th>Никнейм</th>
                  <th>Роль</th>
                  <th>Отчетов</th>
                  <th>Дата регистрации</th>
                  <th>Действия</th>
                </tr>
              </thead>
              <tbody id="usersTableBody">
                <!-- Пользователи будут загружены через JavaScript -->
              </tbody>
            </table>
          </div>
        </div>

        <!-- Вкладка статистики -->
        <div class="admin-content" id="adminStatistics">
          <h3>Статистика отчетов</h3>
          
          <div class="chart-container">
            <div class="chart-placeholder" id="reportsChart">
              График загрузки отчетов по неделям
            </div>
          </div>
          
          <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 20px;">
            <div class="admin-section">
              <h4>Распределение по типам отчетов</h4>
              <div id="reportTypesChart" class="chart-placeholder" style="height: 200px;">
                Круговая диаграмма типов отчетов
              </div>
            </div>
            
            <div class="admin-section">
              <h4>Активность пользователей</h4>
              <div id="userActivityChart" class="chart-placeholder" style="height: 200px;">
                График активности пользователей
              </div>
            </div>
          </div>
        </div>

        <!-- Вкладка настроек -->
        <div class="admin-content" id="adminSettings">
          <h3>Настройки системы</h3>
          
          <div class="admin-section">
            <h4>Параметры отчетов</h4>
            <div class="form-grid">
              <div>
                <label class="small muted">Минимальный балл для премии</label>
                <input type="number" id="minAwardPoints" value="250" min="0">
              </div>
              <div>
                <label class="small muted">Недельная норма</label>
                <input type="number" id="weeklyNorm" value="150" min="0">
              </div>
              <div>
                <label class="small muted">Автоодобрение отчетов</label>
                <select id="autoApprove">
                  <option value="true">Включено</option>
                  <option value="false">Выключено</option>
                </select>
              </div>
              <div>
                <label class="small muted">Уведомления по email</label>
                <select id="emailNotifications">
                  <option value="true">Включено</option>
                  <option value="false">Выключено</option>
                </select>
              </div>
            </div>
          </div>
          
          <div class="admin-section">
            <h4>Управление ролями</h4>
            <div class="admin-actions">
              <button class="btn btn-primary" onclick="saveSystemSettings()">Сохранить настройки</button>
              <button class="btn btn-ghost" onclick="resetSystemSettings()">Сбросить настройки</button>
              <button class="btn btn-ghost" onclick="exportSystemData()">Экспорт данных</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Модальное окно редактирования отчета -->
    <div class="modal" id="editReportModal">
      <div class="modal-content">
        <div class="modal-header">
          <h3>Редактирование отчета</h3>
          <button class="close-modal" onclick="closeEditReportModal()">×</button>
        </div>
        <div id="editReportForm">
          <!-- Форма будет заполнена через JavaScript -->
        </div>
      </div>
    </div>

    <!-- Модальное окно редактирования пользователя -->
    <div class="modal" id="editUserModal">
      <div class="modal-content">
        <div class="modal-header">
          <h3>Редактирование пользователя</h3>
          <button class="close-modal" onclick="closeEditUserModal()">×</button>
        </div>
        <div id="editUserForm">
          <!-- Форма будет заполнена через JavaScript -->
        </div>
      </div>
    </div>

    <!-- MAIN -->
    <main class="main" role="main" id="mainView">
      <header class="header">
        <div>
          <h1 class="title">Главная страница</h1>
          <div class="subtitle small"><span id="dept">Отдела Поставок</span></div>
        </div>
        <!-- Кнопка авторизации -->
        <button class="auth-button" id="authButton" onclick="handleAuth()">
          <span>🔐</span>
          <span id="authText">Войти</span>
        </button>
       <script>
       (function rotateDept(){
          const list = ['ОП','Отдел Поставок','Желток','Карабин'];
          let i = 0;
          const el = document.getElementById('dept');
          el.textContent = list[0];
          setInterval(()=>{ i = (i+1) % list.length; el.textContent = list[i]; }, 3600);
       })();
       </script>
      </header>

      <section class="grid">

        <!-- Left: reports / missions -->
        <div class="card" id="reports">
          <h2 style="margin-bottom:12px">Информация</h2>

          <div class="mission-list" id="missionList">
            <!-- Example items (динамически) -->
            <div class="mission">
              <div class="left">
                <div class="mission-icon" style="background:linear-gradient(135deg,#11ff00)">250</div>
                <div>
                  <div style="font-weight:700">Норма на премию</div>
                  <div class="small">Кол-во баллов на премию</div>
                </div>
              </div>
            </div>

            <div class="mission">
              <div class="left">
                <div class="mission-icon" style="background:linear-gradient(135deg,#ff0000)">150</div>
                <div>
                  <div style="font-weight:700">Норма недели</div>
                  <div class="small">Норма</div>
                </div>
              </div>
            </div>

            <!-- add more mission items if needed -->
          </div>

          <hr style="margin:16px 0;border:none;border-top:1px solid rgba(255,255,255,0.03)" />
        </div>

        <!-- Right: stats -->
        <aside class="card" id="info" style="min-width:320px">
          <h2 style="margin-bottom:12px">Статистика</h2>

          <div class="stats-grid" style="margin-bottom:14px">
            <div class="stat">
              <div class="num" id="statReports" aria-live="polite">0</div>
              <div class="lbl">Всего отчетов</div>
            </div>
            <div class="stat">
              <div class="num" id="statOnline">Online</div>
              <div class="lbl">Статус</div>
            </div>
            <div class="stat">
              <div class="num" id="statAward">250</div>
              <div class="lbl">Баллов на премию</div>
            </div>
          </div>

            <hr style="margin:14px 0;border:none;border-top:1px solid rgba(255,255,255,0.03)" />

            <div class="small" style="margin-bottom:8px">Быстрые действия</div>
            <div style="display:flex;gap:8px;flex-wrap:wrap">
              <button class="button ghost" onclick="openDocs()">Открыть логи</button>
              <button class="button ghost" onclick="openSupport()">Связаться с поддержкой</button>
            </div>
          </div>
        </aside>

      </section>

    </main>

  </div>
</div>

<!-- Particles canvas -->
<canvas id="c" style="position:fixed;pointer-events:none;inset:0;z-index:0;opacity:0.06"></canvas>

<script>
// ==================== СИСТЕМА АВТОРИЗАЦИИ ====================
const USER_STORAGE_KEY = 'op_user_session';
const USERS_STORAGE_KEY = 'op_users_database';
let currentUser = null;

// Инициализация
document.addEventListener('DOMContentLoaded', function() {
  initializeApp();
});

function initializeApp() {
  checkAuthStatus();
  setupEventListeners();
  showMainView();
}

// Проверка статуса авторизации
function checkAuthStatus() {
  const stored = localStorage.getItem(USER_STORAGE_KEY);
  if (stored) {
    try {
      currentUser = JSON.parse(stored);
      updateUIForLoggedInUser();
    } catch (e) {
      localStorage.removeItem(USER_STORAGE_KEY);
    }
  }
}

// Настройка обработчиков событий
function setupEventListeners() {
  // Форма авторизации
  document.getElementById('loginForm').addEventListener('submit', function(e) {
    e.preventDefault();
    handleAuthSubmit();
  });
}

// Переключение вкладок авторизации
function switchAuthTab(tab) {
  const loginTab = document.querySelectorAll('.auth-tab')[0];
  const registerTab = document.querySelectorAll('.auth-tab')[1];
  const registerFields = document.getElementById('registerFields');
  const nicknameField = document.getElementById('nicknameField');
  const confirmPasswordField = document.getElementById('confirmPasswordField');
  const rememberMe = document.getElementById('rememberMe');
  const submitBtn = document.getElementById('authSubmitBtn');
  const title = document.getElementById('authModalTitle');
  const subtitle = document.getElementById('authModalSubtitle');

  if (tab === 'login') {
    loginTab.classList.add('active');
    registerTab.classList.remove('active');
    registerFields.style.display = 'none';
    nicknameField.style.display = 'none';
    confirmPasswordField.style.display = 'none';
    rememberMe.style.display = 'flex';
    submitBtn.textContent = 'Войти в систему';
    title.textContent = 'Вход в систему';
    subtitle.textContent = 'Войдите в ваш аккаунт';
  } else {
    loginTab.classList.remove('active');
    registerTab.classList.add('active');
    registerFields.style.display = 'block';
    nicknameField.style.display = 'block';
    confirmPasswordField.style.display = 'block';
    rememberMe.style.display = 'none';
    submitBtn.textContent = 'Создать аккаунт';
    title.textContent = 'Регистрация';
    subtitle.textContent = 'Создайте новый аккаунт';
  }
}

// Обработка отправки формы
function handleAuthSubmit() {
  const isLoginMode = document.querySelector('.auth-tab.active').textContent === 'Вход';
  
  if (isLoginMode) {
    handleLogin();
  } else {
    handleRegistration();
  }
}

// Вход в систему
function handleLogin() {
  const email = document.getElementById('authEmail').value.trim();
  const password = document.getElementById('authPassword').value;

  if (!email || !password) {
    showNotification('Заполните все поля', 'error');
    return;
  }

  const users = getUsers();
  const user = users.find(u => u.email === email && u.password === password);

  if (!user) {
    showNotification('Неверный email или пароль', 'error');
    return;
  }

  // Успешный вход
  currentUser = user;
  localStorage.setItem(USER_STORAGE_KEY, JSON.stringify(user));
  updateUIForLoggedInUser();
  closeLoginModal();
  showNotification(`Добро пожаловать, ${user.name}! 🎉`, 'success');
}

// Регистрация
function handleRegistration() {
  const name = document.getElementById('registerName').value.trim();
  const email = document.getElementById('authEmail').value.trim();
  const nickname = document.getElementById('registerNickname').value.trim();
  const password = document.getElementById('authPassword').value;
  const confirmPassword = document.getElementById('confirmPassword').value;

  // Валидация
  if (!name || !email || !nickname || !password || !confirmPassword) {
    showNotification('Заполните все поля', 'error');
    return;
  }

  if (!isValidEmail(email)) {
    showNotification('Введите корректный email', 'error');
    return;
  }

  if (password !== confirmPassword) {
    showNotification('Пароли не совпадают', 'error');
    return;
  }

  if (password.length < 6) {
    showNotification('Пароль должен содержать минимум 6 символов', 'error');
    return;
  }

  const users = getUsers();

  // Проверка существующего пользователя
  if (users.find(u => u.email === email)) {
    showNotification('Пользователь с таким email уже существует', 'error');
    return;
  }

  // Создание нового пользователя
  const newUser = {
    id: generateUserId(),
    name: name,
    email: email,
    nickname: nickname,
    password: password,
    role: 'user',
    registrationDate: new Date().toLocaleDateString('ru-RU'),
    reportsCount: 0,
    rating: 'Новичок',
    loginStreak: 1,
    profileComplete: false,
    examPassed: false,
    contactedSupport: false,
    hasAvatar: false,
    framesTried: 1,
    backgroundsTried: 1,
    lastLogin: new Date().toISOString()
  };

  users.push(newUser);
  localStorage.setItem(USERS_STORAGE_KEY, JSON.stringify(users));
  
  currentUser = newUser;
  localStorage.setItem(USER_STORAGE_KEY, JSON.stringify(newUser));
  
  updateUIForLoggedInUser();
  closeLoginModal();
  showNotification(`Аккаунт создан! Добро пожаловать, ${name}! 🚀`, 'success');
}

// Получение списка пользователей
function getUsers() {
  const users = localStorage.getItem(USERS_STORAGE_KEY);
  return users ? JSON.parse(users) : [];
}

// Генерация ID пользователя
function generateUserId() {
  return 'OP-' + Date.now() + '-' + Math.random().toString(36).substr(2, 9);
}

// Валидация email
function isValidEmail(email) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}

// Обновление UI для авторизованного пользователя
function updateUIForLoggedInUser() {
  const authButton = document.getElementById('authButton');
  const authText = document.getElementById('authText');
  
  if (currentUser) {
    authButton.classList.add('authenticated');
    authText.textContent = currentUser.nickname;
    
    // Обновляем аватар в шапке
    const savedAvatar = localStorage.getItem('op_user_avatar');
    if (savedAvatar) {
      authButton.innerHTML = `
        <div class="user-info">
          <div class="user-avatar">
            <img src="${savedAvatar}" alt="Аватар" style="width:100%;height:100%;border-radius:50%;object-fit:cover;" />
          </div>
          <span id="authText">${currentUser.nickname}</span>
        </div>
      `;
    } else {
      authButton.innerHTML = `
        <div class="user-info">
          <div class="user-avatar">${getInitials(currentUser.nickname)}</div>
          <span id="authText">${currentUser.nickname}</span>
        </div>
      `;
    }
    
    // Обновляем профиль если он открыт
    if (document.getElementById('profileView').style.display === 'block') {
      updateProfileInfo();
      updateAchievements();
    }
  } else {
    authButton.classList.remove('authenticated');
    authText.textContent = 'Войти';
    authButton.innerHTML = '<span>🔐</span><span id="authText">Войти</span>';
  }
}

// Выход из системы
function logout() {
  currentUser = null;
  localStorage.removeItem(USER_STORAGE_KEY);
  
  const authButton = document.getElementById('authButton');
  authButton.classList.remove('authenticated');
  authText.textContent = 'Войти';
  authButton.innerHTML = '<span>🔐</span><span id="authText">Войти</span>';
  
  showNotification('Вы вышли из системы', 'info');
}

// ==================== СИСТЕМА ПРОСМОТРОВ ====================
function showMainView() {
  document.getElementById('mainView').style.display = 'flex';
  document.getElementById('profileView').style.display = 'none';
  document.getElementById('createView').style.display = 'none';
  document.getElementById('examView').style.display = 'none';
  document.getElementById('adminView').style.display = 'none';
}

function showProfileView() {
  document.getElementById('mainView').style.display = 'none';
  document.getElementById('profileView').style.display = 'block';
  document.getElementById('createView').style.display = 'none';
  document.getElementById('examView').style.display = 'none';
  document.getElementById('adminView').style.display = 'none';
  
  // Обновляем информацию профиля при открытии
  updateProfileInfo();
  // Обновляем достижения
  updateAchievements();
  // Инициализируем выбор рамок
  initFrameSelection();
  // Инициализируем выбор фона
  initBackgroundSelection();
}

function showCreateView() {
  document.getElementById('mainView').style.display = 'none';
  document.getElementById('profileView').style.display = 'none';
  document.getElementById('createView').style.display = 'block';
  document.getElementById('examView').style.display = 'none';
  document.getElementById('adminView').style.display = 'none';
  
  // Инициализируем обработчики для формы создания отчета
  initCreateForm();
}

function showExamView() {
  document.getElementById('mainView').style.display = 'none';
  document.getElementById('profileView').style.display = 'none';
  document.getElementById('createView').style.display = 'none';
  document.getElementById('examView').style.display = 'block';
  document.getElementById('adminView').style.display = 'none';
}

function showAdminView() {
  // Проверяем права доступа
  if (!currentUser || (currentUser.role !== 'admin' && currentUser.role !== 'moderator')) {
    showNotification('Доступ запрещен. Требуются права администратора или модератора.', 'error');
    return;
  }
  
  document.getElementById('mainView').style.display = 'none';
  document.getElementById('profileView').style.display = 'none';
  document.getElementById('createView').style.display = 'none';
  document.getElementById('examView').style.display = 'none';
  document.getElementById('adminView').style.display = 'block';
  
  // Загружаем данные для админ-панели
  loadAdminData();
}

function handleKeyPress(event, view) {
  if (event.key === 'Enter' || event.key === ' ') {
    event.preventDefault();
    switch(view) {
      case 'main': showMainView(); break;
      case 'profile': showProfileView(); break;
      case 'create': showCreateView(); break;
      case 'exam': showExamView(); break;
      case 'admin': showAdminView(); break;
    }
  }
}

// ==================== СИСТЕМА АДМИН-ПАНЕЛИ ====================

// Загрузка данных для админ-панели
function loadAdminData() {
  loadAdminStats();
  loadReportsTable();
  loadUsersTable();
  loadStatisticsCharts();
}

// Загрузка статистики
function loadAdminStats() {
  const reports = JSON.parse(localStorage.getItem('op_reports') || '[]');
  const users = getUsers();
  
  const totalReports = reports.length;
  const totalUsers = users.length;
  const pendingReports = reports.filter(r => r.status === 'pending').length;
  const avgPoints = reports.length > 0 ? 
    Math.round(reports.reduce((sum, r) => sum + (parseInt(r.points) || 0), 0) / reports.length) : 0;
  
  document.getElementById('adminTotalReports').textContent = totalReports;
  document.getElementById('adminTotalUsers').textContent = totalUsers;
  document.getElementById('adminPendingReports').textContent = pendingReports;
  document.getElementById('adminAvgPoints').textContent = avgPoints;
}

// Загрузка таблицы отчетов
function loadReportsTable() {
  const reports = JSON.parse(localStorage.getItem('op_reports') || '[]');
  const tbody = document.getElementById('reportsTableBody');
  
  tbody.innerHTML = '';
  
  reports.forEach(report => {
    const row = document.createElement('tr');
    const statusClass = `status-${report.status || 'pending'}`;
    const statusText = getStatusText(report.status);
    
    row.innerHTML = `
      <td>${report.id || 'N/A'}</td>
      <td>${report.title || 'Без названия'}</td>
      <td>${report.author || 'Неизвестно'}</td>
      <td>${getReportTypeText(report.type)}</td>
      <td>${new Date(report.timestamp).toLocaleDateString('ru-RU')}</td>
      <td>${report.points || 0}</td>
      <td><span class="status-badge ${statusClass}">${statusText}</span></td>
      <td>
        <button class="action-btn edit" onclick="editReport('${report.id}')">✏️</button>
        <button class="action-btn approve" onclick="approveReport('${report.id}')">✅</button>
        <button class="action-btn reject" onclick="rejectReport('${report.id}')">❌</button>
        <button class="action-btn delete" onclick="deleteReport('${report.id}')">🗑️</button>
      </td>
    `;
    
    tbody.appendChild(row);
  });
}

// Загрузка таблицы пользователей
function loadUsersTable() {
  const users = getUsers();
  const tbody = document.getElementById('usersTableBody');
  
  tbody.innerHTML = '';
  
  users.forEach(user => {
    const row = document.createElement('tr');
    const roleClass = `role-${user.role || 'user'}`;
    const roleText = getRoleText(user.role);
    
    row.innerHTML = `
      <td>${user.id}</td>
      <td>${user.name}</td>
      <td>${user.email}</td>
      <td>${user.nickname}</td>
      <td><span class="role-badge ${roleClass}">${roleText}</span></td>
      <td>${user.reportsCount || 0}</td>
      <td>${user.registrationDate}</td>
      <td>
        <button class="action-btn edit" onclick="editUser('${user.id}')">✏️</button>
        <button class="action-btn delete" onclick="deleteUser('${user.id}')">🗑️</button>
      </td>
    `;
    
    tbody.appendChild(row);
  });
}

// Загрузка графиков статистики
function loadStatisticsCharts() {
  // В реальном приложении здесь были бы реальные графики
  // Для демонстрации используем заполнители
  
  const reportsChart = document.getElementById('reportsChart');
  const reportTypesChart = document.getElementById('reportTypesChart');
  const userActivityChart = document.getElementById('userActivityChart');
  
  reportsChart.innerHTML = '📊 График загрузки отчетов по неделям (здесь будет реальный график)';
  reportTypesChart.innerHTML = '📈 Распределение по типам отчетов (здесь будет круговая диаграмма)';
  userActivityChart.innerHTML = '👥 Активность пользователей (здесь будет график активности)';
}

// Переключение вкладок админ-панели
function switchAdminTab(tabName) {
  // Скрываем все вкладки
  document.querySelectorAll('.admin-content').forEach(tab => {
    tab.classList.remove('active');
  });
  
  // Убираем активный класс со всех вкладок
  document.querySelectorAll('.admin-tab').forEach(tab => {
    tab.classList.remove('active');
  });
  
  // Показываем выбранную вкладку
  document.getElementById('admin' + capitalizeFirst(tabName)).classList.add('active');
  
  // Активируем соответствующую кнопку
  document.querySelector(`.admin-tab[onclick="switchAdminTab('${tabName}')"]`).classList.add('active');
}

// Вспомогательные функции для админ-панели
function getStatusText(status) {
  const statusMap = {
    'pending': 'Ожидает',
    'approved': 'Одобрено',
    'rejected': 'Отклонено'
  };
  return statusMap[status] || 'Ожидает';
}

function getReportTypeText(type) {
  const typeMap = {
    'weekly': 'Еженедельный',
    'promotion': 'На повышение'
  };
  return typeMap[type] || 'Неизвестно';
}

function getRoleText(role) {
  const roleMap = {
    'admin': 'Администратор',
    'moderator': 'Модератор',
    'user': 'Пользователь',
    'guest': 'Гость'
  };
  return roleMap[role] || 'Пользователь';
}

function capitalizeFirst(string) {
  return string.charAt(0).toUpperCase() + string.slice(1);
}

// Действия с отчетами
function editReport(reportId) {
  showNotification(`Редактирование отчета ${reportId}`, 'info');
  // В реальном приложении здесь было бы открытие модального окна редактирования
}

function approveReport(reportId) {
  const reports = JSON.parse(localStorage.getItem('op_reports') || '[]');
  const reportIndex = reports.findIndex(r => r.id === reportId);
  
  if (reportIndex !== -1) {
    reports[reportIndex].status = 'approved';
    localStorage.setItem('op_reports', JSON.stringify(reports));
    loadReportsTable();
    loadAdminStats();
    showNotification('Отчет одобрен', 'success');
  }
}

function rejectReport(reportId) {
  const reports = JSON.parse(localStorage.getItem('op_reports') || '[]');
  const reportIndex = reports.findIndex(r => r.id === reportId);
  
  if (reportIndex !== -1) {
    reports[reportIndex].status = 'rejected';
    localStorage.setItem('op_reports', JSON.stringify(reports));
    loadReportsTable();
    loadAdminStats();
    showNotification('Отчет отклонен', 'info');
  }
}

function deleteReport(reportId) {
  if (confirm('Вы уверены, что хотите удалить этот отчет?')) {
    const reports = JSON.parse(localStorage.getItem('op_reports') || '[]');
    const filteredReports = reports.filter(r => r.id !== reportId);
    localStorage.setItem('op_reports', JSON.stringify(filteredReports));
    loadReportsTable();
    loadAdminStats();
    showNotification('Отчет удален', 'info');
  }
}

// Действия с пользователями
function editUser(userId) {
  showNotification(`Редактирование пользователя ${userId}`, 'info');
  // В реальном приложении здесь было бы открытие модального окна редактирования
}

function deleteUser(userId) {
  if (confirm('Вы уверены, что хотите удалить этого пользователя?')) {
    const users = getUsers();
    const filteredUsers = users.filter(u => u.id !== userId);
    localStorage.setItem(USERS_STORAGE_KEY, JSON.stringify(filteredUsers));
    loadUsersTable();
    loadAdminStats();
    showNotification('Пользователь удален', 'info');
  }
}

// Фильтрация отчетов
function filterReports() {
  const searchTerm = document.getElementById('reportSearch').value.toLowerCase();
  const typeFilter = document.getElementById('reportTypeFilter').value;
  const statusFilter = document.getElementById('reportStatusFilter').value;
  
  const rows = document.querySelectorAll('#reportsTableBody tr');
  
  rows.forEach(row => {
    const title = row.cells[1].textContent.toLowerCase();
    const author = row.cells[2].textContent.toLowerCase();
    const type = row.cells[3].textContent;
    const status = row.cells[6].querySelector('.status-badge').textContent;
    
    const matchesSearch = title.includes(searchTerm) || author.includes(searchTerm);
    const matchesType = typeFilter === 'all' || 
      (typeFilter === 'weekly' && type === 'Еженедельный') ||
      (typeFilter === 'promotion' && type === 'На повышение');
    const matchesStatus = statusFilter === 'all' || 
      (statusFilter === 'pending' && status === 'Ожидает') ||
      (statusFilter === 'approved' && status === 'Одобрено') ||
      (statusFilter === 'rejected' && status === 'Отклонено');
    
    row.style.display = matchesSearch && matchesType && matchesStatus ? '' : 'none';
  });
}

// Фильтрация пользователей
function filterUsers() {
  const searchTerm = document.getElementById('userSearch').value.toLowerCase();
  const roleFilter = document.getElementById('userRoleFilter').value;
  
  const rows = document.querySelectorAll('#usersTableBody tr');
  
  rows.forEach(row => {
    const name = row.cells[1].textContent.toLowerCase();
    const email = row.cells[2].textContent.toLowerCase();
    const nickname = row.cells[3].textContent.toLowerCase();
    const role = row.cells[4].querySelector('.role-badge').textContent;
    
    const matchesSearch = name.includes(searchTerm) || email.includes(searchTerm) || nickname.includes(searchTerm);
    const matchesRole = roleFilter === 'all' || 
      (roleFilter === 'admin' && role === 'Администратор') ||
      (roleFilter === 'moderator' && role === 'Модератор') ||
      (roleFilter === 'user' && role === 'Пользователь') ||
      (roleFilter === 'guest' && role === 'Гость');
    
    row.style.display = matchesSearch && matchesRole ? '' : 'none';
  });
}

// Настройки системы
function saveSystemSettings() {
  const minAwardPoints = document.getElementById('minAwardPoints').value;
  const weeklyNorm = document.getElementById('weeklyNorm').value;
  const autoApprove = document.getElementById('autoApprove').value;
  const emailNotifications = document.getElementById('emailNotifications').value;
  
  const settings = {
    minAwardPoints,
    weeklyNorm,
    autoApprove,
    emailNotifications,
    lastUpdated: new Date().toISOString()
  };
  
  localStorage.setItem('op_system_settings', JSON.stringify(settings));
  showNotification('Настройки системы сохранены', 'success');
}

function resetSystemSettings() {
  if (confirm('Вы уверены, что хотите сбросить настройки системы?')) {
    document.getElementById('minAwardPoints').value = '250';
    document.getElementById('weeklyNorm').value = '150';
    document.getElementById('autoApprove').value = 'false';
    document.getElementById('emailNotifications').value = 'true';
    showNotification('Настройки сброшены к значениям по умолчанию', 'info');
  }
}

function exportSystemData() {
  const reports = JSON.parse(localStorage.getItem('op_reports') || '[]');
  const users = getUsers();
  const settings = JSON.parse(localStorage.getItem('op_system_settings') || '{}');
  
  const exportData = {
    reports,
    users,
    settings,
    exportDate: new Date().toISOString()
  };
  
  const dataStr = JSON.stringify(exportData, null, 2);
  const dataBlob = new Blob([dataStr], {type: 'application/json'});
  
  const url = URL.createObjectURL(dataBlob);
  const link = document.createElement('a');
  link.href = url;
  link.download = `op_system_export_${new Date().toISOString().split('T')[0]}.json`;
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
  URL.revokeObjectURL(url);
  
  showNotification('Данные системы экспортированы', 'success');
}

// ==================== УПРАВЛЕНИЕ ПАРОЛЕМ В ПРОФИЛЕ ====================
let passwordVisible = false;

// Функция для переключения видимости пароля
function togglePasswordVisibility() {
  const passwordElement = document.getElementById('profilePassword');
  const toggleButton = document.getElementById('togglePasswordBtn');
  
  if (passwordVisible) {
    // Скрываем пароль
    passwordElement.textContent = '••••••••';
    toggleButton.innerHTML = '👁️ Показать';
    passwordVisible = false;
  } else {
    // Показываем пароль
    if (currentUser && currentUser.password) {
      passwordElement.textContent = currentUser.password;
      toggleButton.innerHTML = '👁️ Скрыть';
      passwordVisible = true;
    } else {
      showNotification('Пароль не установлен', 'info');
    }
  }
}

// Функция для изменения пароля
function changePassword() {
  if (!currentUser) {
    showNotification('Сначала войдите в систему', 'error');
    return;
  }
  
  // Запрашиваем старый пароль для подтверждения
  const oldPassword = prompt('Введите текущий пароль для подтверждения:');
  if (oldPassword === null) return; // Пользователь отменил ввод
  
  if (oldPassword !== currentUser.password) {
    showNotification('Неверный текущий пароль', 'error');
    return;
  }
  
  const newPassword = prompt('Введите новый пароль:');
  if (newPassword === null) return; // Пользователь отменил ввод
  
  if (!newPassword.trim()) {
    showNotification('Пароль не может быть пустым', 'error');
    return;
  }
  
  if (newPassword.length < 4) {
    showNotification('Пароль должен содержать минимум 4 символа', 'error');
    return;
  }
  
  // Подтверждение нового пароля
  const confirmPassword = prompt('Повторите новый пароль:');
  if (confirmPassword === null) return;
  
  if (newPassword !== confirmPassword) {
    showNotification('Пароли не совпадают', 'error');
    return;
  }
  
  // Обновляем пароль
  currentUser.password = newPassword;
  
  // Сохраняем обновленные данные пользователя
  if (localStorage.getItem(USER_STORAGE_KEY)) {
    localStorage.setItem(USER_STORAGE_KEY, JSON.stringify(currentUser));
  }
  
  // Обновляем отображение
  if (passwordVisible) {
    document.getElementById('profilePassword').textContent = newPassword;
  }
  
  showNotification('Пароль успешно изменен!', 'success');
}

// Функция для обновления отображения пароля в профиле
function updatePasswordDisplay() {
  const passwordElement = document.getElementById('profilePassword');
  
  if (currentUser && currentUser.password) {
    if (passwordVisible) {
      passwordElement.textContent = currentUser.password;
    } else {
      passwordElement.textContent = '••••••••';
    }
  } else {
    passwordElement.textContent = '••••••••';
  }
}

// ==================== СИСТЕМА ВЫБОРА ФОНА ====================
const BACKGROUND_THEMES = [
  {
    id: 'stars',
    name: 'Звездное небо',
    icon: '⭐',
    color: 'linear-gradient(135deg, #0b0b0c, #1a1a2e)',
    create: createStars
  },
  {
    id: 'snow',
    name: 'Снегопад',
    icon: '❄️',
    color: 'linear-gradient(135deg, #0b0b0c, #2d3b52)',
    create: createSnowfall
  },
  {
    id: 'confetti',
    name: 'Конфетти',
    icon: '🎉',
    color: 'linear-gradient(135deg, #0b0b0c, #4a235a)',
    create: createConfetti
  },
  {
    id: 'halloween',
    name: 'Хэллоуин',
    icon: '🎃',
    color: 'linear-gradient(135deg, #0b0b0c, #4a235a)',
    create: createHalloween
  },
  {
    id: 'default',
    name: 'Стандартный',
    icon: '🌌',
    color: 'linear-gradient(135deg, #0b0b0c, #1a1a2e)',
    create: function() { /* Ничего не создаем для стандартного фона */ }
  }
];

const BACKGROUND_STORAGE_KEY = 'op_user_background';

// Инициализация выбора фона
function initBackgroundSelection() {
  const backgroundSelection = document.getElementById('backgroundSelection');
  if (!backgroundSelection) return;

  backgroundSelection.innerHTML = '';

  BACKGROUND_THEMES.forEach(theme => {
    const backgroundOption = document.createElement('div');
    backgroundOption.className = 'background-option';
    backgroundOption.title = theme.name;
    backgroundOption.dataset.themeId = theme.id;
    backgroundOption.dataset.themeName = theme.name;

    backgroundOption.innerHTML = `
      <div class="background-preview" style="background: ${theme.color}">
        ${theme.icon}
      </div>
      <div>${theme.name}</div>
    `;

    backgroundOption.addEventListener('click', () => selectBackground(theme.id, theme.name));
    backgroundSelection.appendChild(backgroundOption);
  });

  // Загружаем сохраненный фон
  loadSavedBackground();
}

// Выбор фона
function selectBackground(themeId, themeName) {
  // Скрываем все фоны
  hideAllBackgrounds();
  
  // Показываем выбранный фон
  if (themeId !== 'default') {
    const theme = BACKGROUND_THEMES.find(t => t.id === themeId);
    if (theme && theme.create) {
      theme.create();
    }
  }
  
  // Обновляем активный элемент в выборе фонов
  updateActiveBackground(themeId);
  
  // Обновляем информацию о текущем фоне
  const currentBackgroundElement = document.getElementById('currentBackground');
  if (currentBackgroundElement) {
    currentBackgroundElement.textContent = themeName;
  }
  
  // Сохраняем выбор в localStorage
  localStorage.setItem(BACKGROUND_STORAGE_KEY, JSON.stringify({
    id: themeId,
    name: themeName
  }));
  
  showNotification(`Фон "${themeName}" применен!`, 'success');
}

// Скрытие всех фонов
function hideAllBackgrounds() {
  const stars = document.getElementById('stars');
  const snowflakes = document.getElementById('snowflakes');
  const confetti = document.getElementById('confetti');
  const halloween = document.getElementById('halloween');
  
  if (stars) stars.innerHTML = '';
  if (snowflakes) snowflakes.innerHTML = '';
  if (confetti) confetti.innerHTML = '';
  if (halloween) halloween.innerHTML = '';
}

// Обновление активного фона в выборе
function updateActiveBackground(activeThemeId) {
  const backgroundOptions = document.querySelectorAll('.background-option');
  backgroundOptions.forEach(option => {
    if (option.dataset.themeId === activeThemeId) {
      option.classList.add('active');
    } else {
      option.classList.remove('active');
    }
  });
}

// Загрузка сохраненного фона
function loadSavedBackground() {
  const savedBackground = localStorage.getItem(BACKGROUND_STORAGE_KEY);
  if (savedBackground) {
    try {
      const backgroundData = JSON.parse(savedBackground);
      selectBackground(backgroundData.id, backgroundData.name);
    } catch (e) {
      console.error('Ошибка загрузки сохраненного фона:', e);
      // Устанавливаем фон по умолчанию
      selectBackground('stars', 'Звездное небо');
    }
  } else {
    // Устанавливаем фон по умолчанию
    selectBackground('stars', 'Звездное небо');
  }
}

// ==================== ФУНКЦИИ СОЗДАНИЯ ФОНОВ ====================

// Звездное небо
function createStars() {
  const starsContainer = document.getElementById('stars');
  const starCount = 200;
  
  for (let i = 0; i < starCount; i++) {
    const star = document.createElement('div');
    star.classList.add('star');
    
    const size = Math.random() * 2 + 0.5;
    star.style.width = `${size}px`;
    star.style.height = `${size}px`;
    
    star.style.left = `${Math.random() * 100}%`;
    star.style.top = `${Math.random() * 100}%`;
    
    star.style.setProperty('--twinkle-duration', `${Math.random() * 5 + 3}s`);
    star.style.setProperty('--twinkle-delay', `${Math.random() * 5}s`);
    
    starsContainer.appendChild(star);
  }
}

// Снегопад
function createSnowfall() {
  const snowContainer = document.getElementById('snowflakes');
  const snowflakeCount = 150;
  
  for (let i = 0; i < snowflakeCount; i++) {
    const snowflake = document.createElement('div');
    snowflake.classList.add('snowflake');
    
    const size = Math.random() * 4 + 1;
    snowflake.style.width = `${size}px`;
    snowflake.style.height = `${size}px`;
    
    snowflake.style.left = `${Math.random() * 100}%`;
    snowflake.style.top = `${Math.random() * -20}%`;
    
    snowflake.style.opacity = Math.random() * 0.7 + 0.3;
    snowflake.style.animationDuration = `${Math.random() * 10 + 5}s`;
    snowflake.style.animationDelay = `${Math.random() * 5}s`;
    
    snowContainer.appendChild(snowflake);
  }
}

// Конфетти
function createConfetti() {
  const confettiContainer = document.getElementById('confetti');
  const confettiCount = 200;
  const colors = ['#ff0000', '#00ff00', '#0000ff', '#ffff00', '#ff00ff', '#00ffff'];
  
  for (let i = 0; i < confettiCount; i++) {
    const confetti = document.createElement('div');
    confetti.classList.add('confetti-piece');
    
    const color = colors[Math.floor(Math.random() * colors.length)];
    confetti.style.backgroundColor = color;
    
    confetti.style.left = `${Math.random() * 100}%`;
    confetti.style.top = `${Math.random() * -20}%`;
    
    confetti.style.animationDuration = `${Math.random() * 8 + 3}s`;
    confetti.style.animationDelay = `${Math.random() * 5}s`;
    
    // Разные формы конфетти
    if (Math.random() > 0.5) {
      confetti.style.borderRadius = '50%';
    } else {
      confetti.style.transform = `rotate(${Math.random() * 360}deg)`;
    }
    
    confettiContainer.appendChild(confetti);
  }
}

// Хэллоуин
function createHalloween() {
  const halloweenContainer = document.getElementById('halloween');
  const pumpkinCount = 15;
  const batCount = 10;
  
  // Тыквы
  for (let i = 0; i < pumpkinCount; i++) {
    const pumpkin = document.createElement('div');
    pumpkin.classList.add('pumpkin');
    
    pumpkin.style.left = `${Math.random() * 90 + 5}%`;
    pumpkin.style.top = `${Math.random() * 80 + 10}%`;
    
    pumpkin.style.animationDelay = `${Math.random() * 5}s`;
    
    halloweenContainer.appendChild(pumpkin);
  }
  
  // Летучие мыши
  for (let i = 0; i < batCount; i++) {
    const bat = document.createElement('div');
    bat.classList.add('bat');
    bat.textContent = '🦇';
    
    bat.style.left = `${Math.random() * -20}%`;
    bat.style.top = `${Math.random() * 80}%`;
    
    bat.style.animationDuration = `${Math.random() * 15 + 10}s`;
    bat.style.animationDelay = `${Math.random() * 5}s`;
    bat.style.fontSize = `${Math.random() * 10 + 15}px`;
    
    halloweenContainer.appendChild(bat);
  }
}

// ==================== СИСТЕМА РАМОК ДЛЯ АВАТАРОК ====================
const AVATAR_FRAMES = [
  {
    id: 'default',
    name: 'По умолчанию',
    class: 'avatar-frame-default',
    icon: '⚪'
  },
  {
    id: 'gold',
    name: 'Золотая',
    class: 'avatar-frame-gold',
    icon: '🥇'
  },
  {
    id: 'silver',
    name: 'Серебряная',
    class: 'avatar-frame-silver',
    icon: '🥈'
  },
  {
    id: 'bronze',
    name: 'Бронзовая',
    class: 'avatar-frame-bronze',
    icon: '🥉'
  },
  {
    id: 'gradient',
    name: 'Градиент',
    class: 'avatar-frame-gradient',
    icon: '🌈'
  },
  {
    id: 'dotted',
    name: 'Точечная',
    class: 'avatar-frame-dotted',
    icon: '🔘'
  },
  {
    id: 'dashed',
    name: 'Пунктирная',
    class: 'avatar-frame-dashed',
    icon: '➖'
  },
  {
    id: 'double',
    name: 'Двойная',
    class: 'avatar-frame-double',
    icon: '⏸️'
  },
  {
    id: 'groove',
    name: 'Вдавленная',
    class: 'avatar-frame-groove',
    icon: '⏬'
  },
  {
    id: 'ridge',
    name: 'Рельефная',
    class: 'avatar-frame-ridge',
    icon: '⏫'
  },
  {
    id: 'inset',
    name: 'Внутренняя',
    class: 'avatar-frame-inset',
    icon: '📥'
  },
  {
    id: 'outset',
    name: 'Внешняя',
    class: 'avatar-frame-outset',
    icon: '📤'
  },
  {
    id: 'neon',
    name: 'Неоновая',
    class: 'avatar-frame-neon',
    icon: '💡'
  },
  {
    id: 'rainbow',
    name: 'Радужная',
    class: 'avatar-frame-rainbow',
    icon: '🎨'
  },
  {
    id: 'crystal',
    name: 'Кристальная',
    class: 'avatar-frame-crystal',
    icon: '💎'
  },
  {
    id: 'fire',
    name: 'Огненная',
    class: 'avatar-frame-fire',
    icon: '🔥'
  },
  {
    id: 'ice',
    name: 'Ледяная',
    class: 'avatar-frame-ice',
    icon: '❄️'
  }
];

const FRAME_STORAGE_KEY = 'op_user_avatar_frame';

// Инициализация выбора рамок
function initFrameSelection() {
  const frameSelection = document.getElementById('frameSelection');
  if (!frameSelection) return;

  frameSelection.innerHTML = '';

  AVATAR_FRAMES.forEach(frame => {
    const frameOption = document.createElement('div');
    frameOption.className = `frame-option ${frame.class}`;
    frameOption.title = frame.name;
    frameOption.dataset.frameId = frame.id;
    frameOption.dataset.frameClass = frame.class;
    frameOption.dataset.frameName = frame.name;

    frameOption.innerHTML = `
      <div class="frame-demo">
        ${frame.icon}
      </div>
    `;

    frameOption.addEventListener('click', () => selectFrame(frame.id, frame.class, frame.name));
    frameSelection.appendChild(frameOption);
  });

  // Загружаем сохраненную рамку
  loadSavedFrame();
}

// Выбор рамки
function selectFrame(frameId, frameClass, frameName) {
  const profileAvatar = document.getElementById('profileAvatar');
  const currentFrameElement = document.getElementById('currentFrame');
  
  // Удаляем все классы рамок
  AVATAR_FRAMES.forEach(frame => {
    profileAvatar.classList.remove(frame.class);
  });
  
  // Добавляем выбранную рамку
  profileAvatar.classList.add(frameClass);
  
  // Обновляем активный элемент в выборе рамок
  updateActiveFrame(frameId);
  
  // Обновляем информацию о текущей рамке
  if (currentFrameElement) {
    currentFrameElement.textContent = frameName;
  }
  
  // Сохраняем выбор в localStorage
  localStorage.setItem(FRAME_STORAGE_KEY, JSON.stringify({
    id: frameId,
    class: frameClass,
    name: frameName
  }));
  
  // Обновляем аватар в шапке
  updateHeaderAvatarFrame(frameClass);
  
  showNotification(`Рамка "${frameName}" применена!`, 'success');
}

// Обновление активной рамки в выборе
function updateActiveFrame(activeFrameId) {
  const frameOptions = document.querySelectorAll('.frame-option');
  frameOptions.forEach(option => {
    if (option.dataset.frameId === activeFrameId) {
      option.classList.add('active');
    } else {
      option.classList.remove('active');
    }
  });
}

// Загрузка сохраненной рамки
function loadSavedFrame() {
  const savedFrame = localStorage.getItem(FRAME_STORAGE_KEY);
  if (savedFrame) {
    try {
      const frameData = JSON.parse(savedFrame);
      selectFrame(frameData.id, frameData.class, frameData.name);
    } catch (e) {
      console.error('Ошибка загрузки сохраненной рамки:', e);
      // Устанавливаем рамку по умолчанию
      selectFrame('default', 'avatar-frame-default', 'По умолчанию');
    }
  } else {
    // Устанавливаем рамку по умолчанию
    selectFrame('default', 'avatar-frame-default', 'По умолчанию');
  }
}

// Обновление рамки аватара в шапке
function updateHeaderAvatarFrame(frameClass) {
  const headerAvatar = document.querySelector('.user-avatar');
  if (headerAvatar) {
    // Удаляем все классы рамок
    AVATAR_FRAMES.forEach(frame => {
      headerAvatar.classList.remove(frame.class);
    });
    
    // Добавляем выбранную рамку (упрощенную версию для маленького аватара)
    if (frameClass !== 'avatar-frame-default') {
      headerAvatar.classList.add('avatar-frame-gradient'); // Упрощенная рамка для маленького аватара
    }
  }
}

// ==================== СИСТЕМА ДОСТИЖЕНИЙ ====================
const ACHIEVEMENTS = [
  {
    id: 'first_report',
    name: 'Первый отчет',
    description: 'Отправьте ваш первый отчет',
    icon: '📄',
    condition: (user) => user.reportsCount >= 1,
    progress: (user) => Math.min(user.reportsCount, 1)
  },
  {
    id: 'reporter',
    name: 'Репортер',
    description: 'Отправьте 5 отчетов',
    icon: '📊',
    condition: (user) => user.reportsCount >= 5,
    progress: (user) => Math.min(user.reportsCount / 5, 1)
  },
  {
    id: 'expert',
    name: 'Эксперт',
    description: 'Отправьте 20 отчетов',
    icon: '🏆',
    condition: (user) => user.reportsCount >= 20,
    progress: (user) => Math.min(user.reportsCount / 20, 1)
  },
  {
    id: 'avatar_master',
    name: 'Мастер аватаров',
    description: 'Установите аватар профиля',
    icon: '🖼️',
    condition: (user) => user.hasAvatar || false,
    progress: (user) => user.hasAvatar ? 1 : 0
  },
  {
    id: 'frame_collector',
    name: 'Коллекционер рамок',
    description: 'Попробуйте 5 разных рамок',
    icon: '🖼️',
    condition: (user) => user.framesTried >= 5,
    progress: (user) => Math.min((user.framesTried || 0) / 5, 1)
  },
  {
    id: 'background_master',
    name: 'Мастер фонов',
    description: 'Попробуйте все фоны',
    icon: '🎨',
    condition: (user) => user.backgroundsTried >= BACKGROUND_THEMES.length,
    progress: (user) => Math.min((user.backgroundsTried || 0) / BACKGROUND_THEMES.length, 1)
  },
  {
    id: 'early_bird',
    name: 'Ранняя пташка',
    description: 'Войдите в систему 3 дня подряд',
    icon: '🌅',
    condition: (user) => user.loginStreak >= 3,
    progress: (user) => Math.min((user.loginStreak || 0) / 3, 1)
  },
  {
    id: 'veteran',
    name: 'Ветеран',
    description: 'Войдите в систему 30 дней',
    icon: '🎖️',
    condition: (user) => user.loginStreak >= 30,
    progress: (user) => Math.min((user.loginStreak || 0) / 30, 1)
  },
  {
    id: 'perfectionist',
    name: 'Перфекционист',
    description: 'Получите рейтинг "Эксперт"',
    icon: '⭐',
    condition: (user) => user.rating === 'Эксперт',
    progress: (user) => user.rating === 'Эксперт' ? 1 : 0
  },
  {
    id: 'social',
    name: 'Социальный',
    description: 'Заполните все поля профиля',
    icon: '👥',
    condition: (user) => user.profileComplete || false,
    progress: (user) => user.profileComplete ? 1 : 0
  },
  {
    id: 'quick_learner',
    name: 'Быстрый ученик',
    description: 'Пройдите экзамен с первой попытки',
    icon: '🎓',
    condition: (user) => user.examPassed || false,
    progress: (user) => user.examPassed ? 1 : 0
  },
  {
    id: 'helper',
    name: 'Помощник',
    description: 'Свяжитесь с поддержкой',
    icon: '🤝',
    condition: (user) => user.contactedSupport || false,
    progress: (user) => user.contactedSupport ? 1 : 0
  }
];

function updateAchievements() {
  const achList = document.getElementById('achList');
  const achievementsCount = document.getElementById('achievementsCount');
  const achievementsProgress = document.getElementById('achievementsProgress');
  
  if (!achList) return;

  achList.innerHTML = '';

  let unlockedCount = 0;
  let totalProgress = 0;

  ACHIEVEMENTS.forEach(achievement => {
    const isUnlocked = currentUser ? achievement.condition(currentUser) : false;
    const progress = currentUser ? achievement.progress(currentUser) : 0;
    
    if (isUnlocked) unlockedCount++;
    totalProgress += progress;

    const achElement = document.createElement('div');
    achElement.className = `achievement ${isUnlocked ? '' : 'locked'}`;
    achElement.title = `${achievement.name}: ${achievement.description}`;
    
    achElement.innerHTML = `
      <div class="achievement-icon">${achievement.icon}</div>
      <div class="achievement-content">
        <div class="achievement-name">${achievement.name}</div>
        <div class="achievement-desc">${achievement.description}</div>
        ${!isUnlocked && progress > 0 ? `
          <div class="achievement-progress">
            <div class="achievement-progress-bar" style="width: ${progress * 100}%"></div>
          </div>
        ` : ''}
      </div>
    `;
    
    achList.appendChild(achElement);
  });

  // Обновляем статистику достижений
  if (achievementsCount) {
    achievementsCount.textContent = `${unlockedCount}/${ACHIEVEMENTS.length}`;
  }
  if (achievementsProgress) {
    const progressPercent = Math.round((totalProgress / ACHIEVEMENTS.length) * 100);
    achievementsProgress.textContent = `${progressPercent}% выполнено`;
  }
}

// ==================== СИСТЕМА АВАТАРОК ====================
const AVATAR_STORAGE_KEY = 'op_user_avatar';

function handleAvatarUpload(event) {
  const file = event.target.files[0];
  if (!file) return;

  // Проверяем тип файла
  if (!file.type.startsWith('image/')) {
    showNotification('Пожалуйста, выберите изображение', 'error');
    return;
  }

  // Проверяем размер файла (максимум 5MB)
  if (file.size > 5 * 1024 * 1024) {
    showNotification('Размер файла не должен превышать 5MB', 'error');
    return;
  }

  const reader = new FileReader();
  
  reader.onload = function(e) {
    const avatarData = e.target.result;
    
    // Сохраняем аватар в localStorage
    localStorage.setItem(AVATAR_STORAGE_KEY, avatarData);
    
    // Обновляем отображение аватара
    updateAvatarDisplay(avatarData);
    
    // Обновляем информацию о размере
    updateAvatarSizeInfo(file.size);
    
    // Обновляем достижения
    if (currentUser) {
      currentUser.hasAvatar = true;
      updateAchievements();
    }
    
    showNotification('Аватар успешно загружен!', 'success');
  };
  
  reader.onerror = function() {
    showNotification('Ошибка при загрузке изображения', 'error');
  };
  
  reader.readAsDataURL(file);
}

function removeAvatar() {
  // Удаляем аватар из localStorage
  localStorage.removeItem(AVATAR_STORAGE_KEY);
  
  // Восстанавливаем стандартный аватар
  updateAvatarDisplay(null);
  
  // Сбрасываем информацию о размере
  document.getElementById('avatarSize').textContent = '-';
  
  // Обновляем достижения
  if (currentUser) {
    currentUser.hasAvatar = false;
    updateAchievements();
  }
  
  showNotification('Аватар удален', 'info');
}

function updateAvatarDisplay(avatarData) {
  const avatarElement = document.getElementById('profileAvatar');
  
  if (avatarData) {
    // Показываем загруженное изображение
    avatarElement.innerHTML = `
      <img src="${avatarData}" alt="Аватар пользователя" />
      <div class="avatar-upload">Нажмите для изменения</div>
    `;
    
    // Также обновляем маленький аватар в шапке
    updateHeaderAvatar(avatarData);
  } else {
    // Показываем стандартный аватар с инициалами
    const initials = currentUser ? getInitials(currentUser.nickname) : '?';
    avatarElement.innerHTML = `
      <span>${initials}</span>
      <div class="avatar-upload">Нажмите для загрузки</div>
    `;
    
    // Сбрасываем маленький аватар в шапке
    updateHeaderAvatar(null);
  }
}

function updateHeaderAvatar(avatarData) {
  const headerAvatar = document.querySelector('.user-avatar');
  if (headerAvatar && currentUser) {
    if (avatarData) {
      headerAvatar.innerHTML = `<img src="${avatarData}" alt="Аватар" style="width:100%;height:100%;border-radius:50%;object-fit:cover;" />`;
    } else {
      headerAvatar.textContent = getInitials(currentUser.nickname);
      headerAvatar.style.background = 'linear-gradient(135deg, #667eea, #764ba2)';
    }
  }
}

function updateAvatarSizeInfo(fileSize) {
  const sizeElement = document.getElementById('avatarSize');
  const sizeInKB = Math.round(fileSize / 1024);
  sizeElement.textContent = `${sizeInKB} KB`;
}

function loadSavedAvatar() {
  const savedAvatar = localStorage.getItem(AVATAR_STORAGE_KEY);
  if (savedAvatar) {
    updateAvatarDisplay(savedAvatar);
    if (currentUser) {
      currentUser.hasAvatar = true;
    }
  }
}

// ==================== ОБНОВЛЕНИЕ ИНФОРМАЦИИ ПРОФИЛЯ ====================
function updateProfileInfo() {
  const profileName = document.getElementById('profileName');
  const profileEmail = document.getElementById('profileEmail');
  const profileNickname = document.getElementById('profileNickname');
  const profileId = document.getElementById('profileId');
  const profileStatus = document.getElementById('profileStatus');
  const profileRole = document.getElementById('profileRole');
  const profileRegDate = document.getElementById('profileRegDate');
  const profileAvatar = document.getElementById('profileAvatar');
  const profileAuthBtn = document.getElementById('profileAuthBtn');
  const profileReportsCount = document.getElementById('profileReportsCount');
  const profileLastActivity = document.getElementById('profileLastActivity');
  const profileRating = document.getElementById('profileRating');
  
  if (currentUser) {
    // Пользователь авторизован
    profileName.textContent = currentUser.name || 'Не указано';
    profileEmail.textContent = currentUser.email || 'Не указано';
    profileNickname.textContent = currentUser.nickname || 'Не указано';
    profileId.textContent = currentUser.id || generateUserId(currentUser.email);
    profileStatus.textContent = 'Авторизован';
    profileStatus.style.color = '#10b981';
    profileRole.textContent = getRoleText(currentUser.role) || 'Пользователь';
    profileRegDate.textContent = currentUser.registrationDate || getCurrentDate();
    profileAuthBtn.textContent = 'Выйти из системы';
    
    // Статистика
    profileReportsCount.textContent = currentUser.reportsCount || '0';
    profileLastActivity.textContent = new Date().toLocaleString('ru-RU');
    profileRating.textContent = currentUser.rating || 'Новичок';
    
    // Обновляем отображение пароля
    updatePasswordDisplay();
    
    // Загружаем сохраненный аватар
    loadSavedAvatar();
  } else {
    // Пользователь не авторизован
    profileName.textContent = 'Не авторизован';
    profileEmail.textContent = '-';
    profileNickname.textContent = '-';
    profileId.textContent = '-';
    profileStatus.textContent = 'Не авторизован';
    profileStatus.style.color = '#ef4444';
    profileRole.textContent = 'Гость';
    profileRegDate.textContent = '-';
    profileAuthBtn.textContent = 'Войти в систему';
    
    // Статистика
    profileReportsCount.textContent = '0';
    profileLastActivity.textContent = '-';
    profileRating.textContent = '-';
    
    // Сбрасываем пароль
    document.getElementById('profilePassword').textContent = '••••••••';
    passwordVisible = false;
    document.getElementById('togglePasswordBtn').innerHTML = '👁️ Показать';
    
    // Сбрасываем аватар
    updateAvatarDisplay(null);
  }
}

function getCurrentDate() {
  return new Date().toLocaleDateString('ru-RU');
}

function getInitials(name) {
  if (!name) return '??';
  return name.split(' ').map(n => n[0]).join('').toUpperCase().substring(0, 2);
}

// ==================== АВТОРИЗАЦИЯ ====================
function handleAuth() {
  if (currentUser) {
    // Выход из системы
    logout();
  } else {
    // Открываем модальное окно для входа
    openLoginModal();
  }
}

function openLoginModal() {
  document.getElementById('loginModal').classList.add('active');
  // Очищаем форму при открытии (кроме чекбокса "Запомнить меня")
  document.getElementById('authEmail').value = '';
  document.getElementById('authPassword').value = '';
  // Фокусируемся на первом поле
  setTimeout(() => document.getElementById('authEmail').focus(), 300);
}

function closeLoginModal() {
  document.getElementById('loginModal').classList.remove('active');
}

// Закрытие модального окна при клике вне его
document.getElementById('loginModal').addEventListener('click', function(e) {
  if (e.target === this) {
    closeLoginModal();
  }
});

// Закрытие модального окна по ESC
document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape' && document.getElementById('loginModal').classList.contains('active')) {
    closeLoginModal();
  }
});

// ==================== УТИЛИТЫ ====================
function showNotification(message, type = 'info') {
  // Создаем уведомление
  const notification = document.createElement('div');
  notification.style.cssText = `
    position: fixed;
    top: 20px;
    right: 20px;
    background: ${type === 'success' ? 'linear-gradient(135deg, #10b981, #059669)' : 
                 type === 'error' ? 'linear-gradient(135deg, #ef4444, #dc2626)' : 
                 'linear-gradient(135deg, var(--accent1), var(--accent2))'};
    color: #04111a;
    padding: 12px 16px;
    border-radius: 8px;
    font-weight: 600;
    z-index: 1000;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    transform: translateX(100%);
    transition: transform 0.3s ease;
  `;
  notification.textContent = message;
  document.body.appendChild(notification);
  
  // Анимация появления
  setTimeout(() => notification.style.transform = 'translateX(0)', 10);
  
  // Автоматическое скрытие через 3 секунды
  setTimeout(() => {
    notification.style.transform = 'translateX(100%)';
    setTimeout(() => document.body.removeChild(notification), 300);
  }, 3000);
}

/* -------------------------
   Helper animation utilities
   ------------------------- */
function animateValue(el, start, end, duration = 1000) {
  start = Number(start)||0; end = Number(end)||0;
  if (start === end) return;
  const range = end - start;
  const startTime = performance.now();
  function frame(now){
    const progress = Math.min((now - startTime)/duration, 1);
    const val = Math.floor(start + (range * progress));
    el.textContent = val;
    if (progress < 1) requestAnimationFrame(frame);
  }
  requestAnimationFrame(frame);
}

/* -------------------------
   Particles (canvas) — lightweight
   ------------------------- */
(function initParticles(){
  const canvas = document.getElementById('c');
  const ctx = canvas.getContext('2d');
  let w = canvas.width = innerWidth;
  let h = canvas.height = innerHeight;
  const parts = [];
  const count = Math.floor((w*h)/80000); // responsive density
  for (let i=0;i<count;i++){
    parts.push({
      x: Math.random()*w,
      y: Math.random()*h,
      r: 0.5 + Math.random()*2.2,
      vx: -0.2 + Math.random()*0.4,
      vy: -0.15 + Math.random()*0.15,
      hue: Math.random()*360,
      alpha: 0.05 + Math.random()*0.2
    });
  }
  function resize(){w=canvas.width=innerWidth;h=canvas.height=innerHeight}
  addEventListener('resize', resize);

  function draw(){
    ctx.clearRect(0,0,w,h);
    for (let p of parts){
      p.x += p.vx; p.y += p.vy;
      if (p.x < -10) p.x = w+10;
      if (p.x > w+10) p.x = -10;
      if (p.y < -10) p.y = h+10;
      if (p.y > h+10) p.y = -10;
      ctx.beginPath();
      ctx.fillStyle = `hsla(${p.hue},60%,60%,${p.alpha})`;
      ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fill();
    }
    requestAnimationFrame(draw);
  }
  draw();
})();

// Инициализация при загрузке
document.addEventListener('DOMContentLoaded', function() {
  // Загружаем сохраненный фон
  loadSavedBackground();
  showMainView();
  // Проверяем сохраненную сессию
  checkAuthStatus();
  // Инициализируем форму создания отчета
  initCreateForm();
});

// Вспомогательные функции
function openDocs() {
  showNotification('Функция открытия логов в разработке', 'info');
}

function openSupport() {
  showNotification('Функция связи с поддержкой в разработке', 'info');
}

function scrollToSection(sectionId) {
  showNotification(`Навигация к разделу ${sectionId}`, 'info');
}

// ==================== ИНИЦИАЛИЗАЦИЯ ФОРМЫ СОЗДАНИЯ ОТЧЕТА ====================
function initCreateForm() {
  const typeInput = document.getElementById('typeInput');
  const weeklyFields = document.getElementById('weeklyFields');
  const promotionFields = document.getElementById('promotionFields');
  const calcWeeklyBtn = document.getElementById('calcWeekly');
  const fillTemplateBtn = document.getElementById('fillFromTemplate');
  const submitReportBtn = document.getElementById('submitReport');
  const clearFormBtn = document.getElementById('clearForm');
  
  // Показываем/скрываем поля в зависимости от типа отчета
  if (typeInput && weeklyFields && promotionFields) {
    typeInput.addEventListener('change', function() {
      if (this.value === 'weekly') {
        weeklyFields.style.display = 'block';
        promotionFields.style.display = 'none';
      } else if (this.value === 'promotion') {
        weeklyFields.style.display = 'none';
        promotionFields.style.display = 'block';
      } else {
        weeklyFields.style.display = 'none';
        promotionFields.style.display = 'none';
      }
    });
  }
  
  // Подсчет баллов для еженедельного отчета
  if (calcWeeklyBtn) {
    calcWeeklyBtn.addEventListener('click', calculateWeeklyPoints);
  }
  
  // Заполнение шаблона
  if (fillTemplateBtn) {
    fillTemplateBtn.addEventListener('click', fillTemplate);
  }
  
  // Отправка отчета
  if (submitReportBtn) {
    submitReportBtn.addEventListener('click', submitReport);
  }
  
  // Очистка формы
  if (clearFormBtn) {
    clearFormBtn.addEventListener('click', clearCreateForm);
  }
}

// Подсчет баллов для еженедельного отчета
function calculateWeeklyPoints() {
  const fields = [
    'm_supply', 'm_reanim', 'm_exam', 'm_inj', 'm_mp', 
    'm_shift', 'm_report', 'm_dispatch', 'm_secondary', 'm_extra'
  ];
  
  let total = 0;
  
  fields.forEach(field => {
    const qty = parseFloat(document.getElementById(`${field}_qty`).value) || 0;
    const pts = parseFloat(document.getElementById(`${field}_pts`).value) || 0;
    total += qty * pts;
  });
  
  document.getElementById('weekly_total').value = Math.round(total);
  showNotification(`Общее количество баллов: ${Math.round(total)}`, 'success');
}

// Заполнение шаблона
function fillTemplate() {
  const typeInput = document.getElementById('typeInput');
  
  if (typeInput.value === 'weekly') {
    // Устанавливаем текущую дату для недели
    const today = new Date();
    const startOfWeek = new Date(today);
    startOfWeek.setDate(today.getDate() - today.getDay() + 1); // Понедельник
    const endOfWeek = new Date(startOfWeek);
    endOfWeek.setDate(startOfWeek.getDate() + 6); // Воскресенье
    
    document.getElementById('weekly_start').value = startOfWeek.toISOString().split('T')[0];
    document.getElementById('weekly_end').value = endOfWeek.toISOString().split('T')[0];
    
    // Устанавливаем стандартные значения баллов
    const standardPoints = {
      'm_supply_pts': 10,
      'm_reanim_pts': 15,
      'm_exam_pts': 8,
      'm_inj_pts': 12,
      'm_mp_pts': 20,
      'm_shift_pts': 2,
      'm_report_pts': 5,
      'm_dispatch_pts': 8,
      'm_secondary_pts': 10,
      'm_extra_pts': 1
    };
    
    Object.keys(standardPoints).forEach(field => {
      document.getElementById(field).value = standardPoints[field];
    });
    
    showNotification('Шаблон еженедельного отчета заполнен', 'info');
  } else if (typeInput.value === 'promotion') {
    // Заполняем шаблон для отчета на повышение
    const today = new Date();
    const threeMonthsAgo = new Date(today);
    threeMonthsAgo.setMonth(today.getMonth() - 3);
    
    document.getElementById('promotion_start_date').value = threeMonthsAgo.toISOString().split('T')[0];
    document.getElementById('promotion_experience').value = '6';
    
    showNotification('Шаблон отчета на повышение заполнен', 'info');
  }
}

// Отправка отчета
function submitReport() {
  const title = document.getElementById('titleInput').value.trim();
  const type = document.getElementById('typeInput').value;
  const description = document.getElementById('descInput').value.trim();
  
  if (!title || !description) {
    showNotification('Заполните обязательные поля: название и описание', 'error');
    return;
  }
  
  // Собираем данные отчета
  const reportData = {
    id: 'RPT-' + Date.now(),
    title,
    type,
    description,
    points: document.getElementById('pointsInput').value || 0,
    timestamp: new Date().toISOString(),
    status: 'pending',
    author: currentUser ? currentUser.nickname : 'Аноним'
  };
  
  // Если это еженедельный отчет, добавляем дополнительные данные
  if (type === 'weekly') {
    reportData.weekly = {
      name: document.getElementById('weekly_name').value,
      startDate: document.getElementById('weekly_start').value,
      endDate: document.getElementById('weekly_end').value,
      vacation: document.querySelector('input[name="weekly_vac"]:checked').value,
      totalPoints: document.getElementById('weekly_total').value
    };
    
    // Добавляем метрики
    const metrics = {};
    const fields = [
      'm_supply', 'm_reanim', 'm_exam', 'm_inj', 'm_mp', 
      'm_shift', 'm_report', 'm_dispatch', 'm_secondary', 'm_extra'
    ];
    
    fields.forEach(field => {
      metrics[field] = {
        quantity: document.getElementById(`${field}_qty`).value || 0,
        points: document.getElementById(`${field}_pts`).value || 0
      };
    });
    
    reportData.weekly.metrics = metrics;
  }
  
  // Если это отчет на повышение, добавляем данные повышения
  if (type === 'promotion') {
    reportData.promotion = {
      name: document.getElementById('promotion_name').value,
      currentPosition: document.getElementById('promotion_current_position').value,
      desiredPosition: document.getElementById('promotion_desired_position').value,
      startDate: document.getElementById('promotion_start_date').value,
      experience: document.getElementById('promotion_experience').value,
      successfulDeliveries: document.getElementById('p_successful_deliveries').value || 0,
      trainingsConducted: document.getElementById('p_trainings_conducted').value || 0,
      mentorships: document.getElementById('p_mentorships').value || 0,
      initiatives: document.getElementById('p_initiatives').value || 0,
      additionalQualification: document.querySelector('input[name="p_qualification"]:checked')?.value || 'no',
      justification: document.getElementById('promotion_justification').value,
      plans: document.getElementById('promotion_plans')?.value || ''
    };
  }
  
  // Сохраняем отчет
  saveReport(reportData);
  
  // Обновляем статистику пользователя
  if (currentUser) {
    currentUser.reportsCount = (currentUser.reportsCount || 0) + 1;
    localStorage.setItem(USER_STORAGE_KEY, JSON.stringify(currentUser));
    updateAchievements();
  }
  
  showNotification('Отчет успешно отправлен!', 'success');
  clearCreateForm();
  showMainView();
}

// Сохранение отчета
function saveReport(reportData) {
  const reports = JSON.parse(localStorage.getItem('op_reports') || '[]');
  reports.push(reportData);
  localStorage.setItem('op_reports', JSON.stringify(reports));
}

// Очистка формы создания отчета
function clearCreateForm() {
  document.getElementById('titleInput').value = '';
  document.getElementById('typeInput').value = 'promotion';
  document.getElementById('descInput').value = '';
  document.getElementById('pointsInput').value = '';
  
  // Очищаем поля еженедельного отчета
  document.getElementById('weekly_name').value = '';
  document.getElementById('weekly_start').value = '';
  document.getElementById('weekly_end').value = '';
  document.getElementById('weekly_total').value = '0';
  
  const weeklyMetricFields = document.querySelectorAll('#weeklyFields input[type="number"]');
  weeklyMetricFields.forEach(field => {
    if (field.id.includes('_qty')) {
      field.value = '0';
    } else if (field.id.includes('_pts') && !field.id.includes('m_extra_pts')) {
      field.value = '0';
    }
  });
  
  document.getElementById('m_extra_pts').value = '1';
  document.querySelector('input[name="weekly_vac"][value="no"]').checked = true;
  
  // Очищаем поля отчета на повышение
  document.getElementById('promotion_name').value = '';
  document.getElementById('promotion_current_position').value = 'intern';
  document.getElementById('promotion_desired_position').value = 'paramedic';
  document.getElementById('promotion_start_date').value = '';
  document.getElementById('promotion_experience').value = '';
  document.getElementById('p_successful_deliveries').value = '0';
  document.getElementById('p_trainings_conducted').value = '0';
  document.getElementById('p_mentorships').value = '0';
  document.getElementById('p_initiatives').value = '0';
  if (document.querySelector('input[name="p_qualification"][value="no"]')) {
    document.querySelector('input[name="p_qualification"][value="no"]').checked = true;
  }
  document.getElementById('promotion_justification').value = '';
  if (document.getElementById('promotion_plans')) {
    document.getElementById('promotion_plans').value = '';
  }
  
  // Скрываем все специфические поля
  document.getElementById('weeklyFields').style.display = 'none';
  document.getElementById('promotionFields').style.display = 'none';
  
  showNotification('Форма очищена', 'info');
}
</script>
</body>
</html>
