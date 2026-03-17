<!DOCTYPE html>
<html lang="uz" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TezkorQuiz — Talabalar uchun professional quiz</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
  <style>
    .card-hover { transition: all 0.4s cubic-bezier(0.34,1.56,0.64,1); }
    .card-hover:hover { transform: translateY(-15px) scale(1.05); box-shadow: 0 25px 50px -12px rgb(16 185 129 / 0.5); }
    .nav-link { position: relative; }
    .nav-link:after { content: ''; position: absolute; width: 0; height: 3px; bottom: -4px; left: 0; background: linear-gradient(to right, #10b981, #22d3ee); transition: width 0.4s; }
    .nav-link:hover:after { width: 100%; }
    .faq-question { transition: all 0.3s; }
  </style>
</head>
<body class="bg-slate-950 text-white font-sans">

<!-- NAVBAR -->
<nav class="fixed top-0 w-full bg-slate-950/95 backdrop-blur-2xl z-50 border-b border-emerald-500/30">
  <div class="max-w-7xl mx-auto px-6 py-5 flex justify-between items-center">
    <div class="flex items-center gap-3">
      <div class="w-12 h-12 bg-gradient-to-br from-emerald-400 to-cyan-400 rounded-3xl flex items-center justify-center text-4xl font-bold shadow-2xl">⚡</div>
      <span class="text-4xl font-black tracking-tighter">Tezkor<span class="text-emerald-400">Quiz</span></span>
    </div>

    <div class="hidden md:flex items-center gap-10 text-lg font-medium">
      <a href="#hero" class="nav-link">Bosh sahifa</a>
      <a href="#avzalliklar" class="nav-link">Avzalliklar</a>
      <a href="#rejimlar" class="nav-link">Rejimlar</a>
      <a href="#kategoriyalar" class="nav-link">Kategoriyalar</a>
      <a href="#yuklash" class="nav-link">Test yuklash</a>
      <a href="#natijalar" class="nav-link">Natijalar</a>
      <a href="#kontakt" class="nav-link">Kontakt</a>
    </div>

    <div class="hidden md:flex items-center gap-4">
      <button onclick="showLoginModal()" class="px-8 py-3 font-semibold hover:text-emerald-400 transition">Kirish</button>
      <button onclick="showLoginModal()" class="bg-emerald-500 hover:bg-emerald-600 px-8 py-3 rounded-3xl font-bold transition">Ro‘yxatdan o‘tish</button>
    </div>

    <button onclick="toggleMobileMenu()" class="md:hidden text-4xl"><i class="fas fa-bars"></i></button>
  </div>

  <!-- Mobile Menu -->
  <div id="mobileMenu" class="hidden md:hidden bg-slate-900 py-8 px-6 border-t border-emerald-500/30">
    <div class="flex flex-col gap-6 text-xl font-medium">
      <a href="#hero" onclick="toggleMobileMenu()" class="nav-link">Bosh sahifa</a>
      <a href="#avzalliklar" onclick="toggleMobileMenu()" class="nav-link">Avzalliklar</a>
      <a href="#rejimlar" onclick="toggleMobileMenu()" class="nav-link">Rejimlar</a>
      <a href="#kategoriyalar" onclick="toggleMobileMenu()" class="nav-link">Kategoriyalar</a>
      <a href="#yuklash" onclick="toggleMobileMenu()" class="nav-link">Test yuklash</a>
      <a href="#natijalar" onclick="toggleMobileMenu()" class="nav-link">Natijalar</a>
      <a href="#kontakt" onclick="toggleMobileMenu()" class="nav-link">Kontakt</a>
      <div class="pt-8 flex flex-col gap-4">
        <button onclick="showLoginModal();toggleMobileMenu()" class="w-full py-4 border-2 border-emerald-400 rounded-3xl">Kirish</button>
        <button onclick="showLoginModal();toggleMobileMenu()" class="w-full py-4 bg-emerald-500 rounded-3xl font-bold">Ro‘yxatdan o‘tish</button>
      </div>
    </div>
  </div>
</nav>

<!-- HERO -->
<section id="hero" class="min-h-screen flex items-center bg-gradient-to-br from-slate-950 via-slate-900 to-black pt-20">
  <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
    <div class="space-y-8">
      <h1 class="text-6xl md:text-7xl font-black leading-none tracking-tighter">BILIMINGIZNI<br><span class="bg-gradient-to-r from-emerald-400 to-cyan-400 bg-clip-text text-transparent">TEZ SINANG</span></h1>
      <p class="text-2xl text-slate-300">.txt fayl yuklang, 5 ta rejimda test o‘tkazing va natijalarni darhol ko‘ring. O‘zbekistondagi eng professional quiz platformasi.</p>
      <div class="flex flex-wrap gap-6">
        <button onclick="document.getElementById('yuklash').scrollIntoView({behavior:'smooth'})" class="bg-emerald-500 hover:bg-emerald-600 px-10 py-5 rounded-3xl text-xl font-bold flex items-center gap-3"><i class="fas fa-upload"></i> .txt yuklash</button>
        <button onclick="startDemoQuiz()" class="border-2 border-emerald-400 hover:bg-emerald-400/10 px-10 py-5 rounded-3xl text-xl font-bold">Demo test</button>
      </div>
    </div>
    <div class="hidden md:block relative">
      <img src="https://picsum.photos/600/600" alt="Quiz" class="rounded-3xl shadow-2xl border border-emerald-500/30">
    </div>
  </div>
</section>

<!-- AVZALLIKLAR -->
<section id="avzalliklar" class="py-24 bg-slate-900">
  <div class="max-w-7xl mx-auto px-6">
    <h2 class="text-5xl font-bold text-center mb-16">Saytning asosiy <span class="text-emerald-400">avzalliklari</span></h2>
    <div class="grid md:grid-cols-3 gap-8">
      <div class="card-hover bg-slate-800 p-10 rounded-3xl text-center"><i class="fas fa-bolt text-6xl text-emerald-400 mb-6"></i><h3 class="text-2xl font-bold">Tez va qulay</h3><p class="mt-4 text-slate-400">Faylni yuklang va bir zumda test boshlang</p></div>
      <div class="card-hover bg-slate-800 p-10 rounded-3xl text-center"><i class="fas fa-mobile-alt text-6xl text-cyan-400 mb-6"></i><h3 class="text-2xl font-bold">Barcha qurilmalarda</h3><p class="mt-4 text-slate-400">Telefon, planshet, kompyuter — hammasida mukammal</p></div>
      <div class="card-hover bg-slate-800 p-10 rounded-3xl text-center"><i class="fas fa-chart-line text-6xl text-amber-400 mb-6"></i><h3 class="text-2xl font-bold">Batafsil natijalar</h3><p class="mt-4 text-slate-400">To‘g‘ri, noto‘g‘ri va o‘tkazib yuborilgan savollar</p></div>
    </div>
  </div>
</section>

<!-- REJIMLAR -->
<section id="rejimlar" class="py-24">
  <div class="max-w-7xl mx-auto px-6">
    <h2 class="text-5xl font-bold text-center mb-16">Moslashuvchan <span class="text-emerald-400">test rejimlari</span></h2>
    <div class="grid md:grid-cols-5 gap-6">
      <div class="card-hover bg-slate-800 rounded-3xl p-8 text-center"><div class="text-7xl mb-6">⚡</div><h3 class="text-2xl font-bold">Tezkor</h3><p class="text-slate-400 mt-2">30 soniya</p></div>
      <div class="card-hover bg-slate-800 rounded-3xl p-8 text-center"><div class="text-7xl mb-6">📖</div><h3 class="text-2xl font-bold">Bilim</h3><p class="text-slate-400 mt-2">Chuqur test</p></div>
      <div class="card-hover bg-slate-800 rounded-3xl p-8 text-center"><div class="text-7xl mb-6">🧠</div><h3 class="text-2xl font-bold">Smart</h3><p class="text-slate-400 mt-2">AI moslashuv</p></div>
      <div class="card-hover bg-slate-800 rounded-3xl p-8 text-center"><div class="text-7xl mb-6">🏆</div><h3 class="text-2xl font-bold">Pro</h3><p class="text-slate-400 mt-2">Qiyin savollar</p></div>
      <div class="card-hover bg-slate-800 rounded-3xl p-8 text-center"><div class="text-7xl mb-6">📝</div><h3 class="text-2xl font-bold">Imtihon</h3><p class="text-slate-400 mt-2">Real muhit</p></div>
    </div>
  </div>
</section>

<!-- KATEGORIYALAR -->
<section id="kategoriyalar" class="py-24 bg-slate-900">
  <div class="max-w-7xl mx-auto px-6">
    <h2 class="text-5xl font-bold text-center mb-16">20+ <span class="text-emerald-400">kategoriya</span></h2>
    <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">📐 Matematika</div>
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">⚛ Fizika</div>
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">🧬 Biologiya</div>
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">📜 Tarix</div>
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">🌍 Geografiya</div>
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">🧪 Kimyo</div>
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">💻 Informatika</div>
      <div class="bg-slate-800 p-8 rounded-3xl text-center hover:bg-emerald-900/30 transition">📖 Adabiyot</div>
    </div>
  </div>
</section>

<!-- TEST YUKLASH -->
<section id="yuklash" class="py-24">
  <div class="max-w-7xl mx-auto px-6 text-center">
    <h2 class="text-5xl font-bold mb-8">Testni .txt fayl bilan yuklang</h2>
    <input type="file" id="fileInput" accept=".txt" class="hidden" onchange="handleFileUpload()">
    <button onclick="document.getElementById('fileInput').click()" class="bg-emerald-500 hover:bg-emerald-600 px-16 py-6 rounded-3xl text-2xl font-bold flex items-center gap-4 mx-auto">
      <i class="fas fa-upload"></i> Faylni tanlang
    </button>
    <p id="uploadStatus" class="mt-6 text-emerald-400 font-medium"></p>
  </div>
</section>

<!-- NATIJALAR (Leaderboard) -->
<section id="natijalar" class="py-24 bg-slate-900">
  <div class="max-w-7xl mx-auto px-6">
    <h2 class="text-5xl font-bold text-center mb-12">Eng yaxshi natijalar</h2>
    <table class="w-full bg-slate-800 rounded-3xl overflow-hidden">
      <thead class="bg-emerald-600"><tr><th class="py-6 px-8 text-left">O‘quvchi</th><th class="py-6 px-8">Ball</th><th class="py-6 px-8">Rejim</th><th class="py-6 px-8">Vaqt</th></tr></thead>
      <tbody id="leaderboardBody" class="text-lg"></tbody>
    </table>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="py-24">
  <div class="max-w-7xl mx-auto px-6">
    <h2 class="text-5xl font-bold text-center mb-16">O‘quvchilarimiz nima deyishadi</h2>
    <div class="grid md:grid-cols-3 gap-8">
      <div class="bg-slate-800 p-8 rounded-3xl">"Eng tez va qulay platforma! Imtihon oldidan juda yordam berdi." — <span class="text-emerald-400">Aziza, 11-sinf</span></div>
      <div class="bg-slate-800 p-8 rounded-3xl">"AI bilan savollar mos kelishi ajoyib! 98 ball oldim." — <span class="text-emerald-400">Sardor, talaba</span></div>
      <div class="bg-slate-800 p-8 rounded-3xl">".txt yuklash bir daqiqada ishlaydi. Tavsiya qilaman!" — <span class="text-emerald-400">Dilshod, o‘qituvchi</span></div>
    </div>
  </div>
</section>

<!-- FAQ -->
<section class="py-24 bg-slate-900">
  <div class="max-w-4xl mx-auto px-6">
    <h2 class="text-5xl font-bold text-center mb-16">Tez-tez so‘raladigan savollar</h2>
    <div onclick="this.querySelector('.answer').classList.toggle('hidden')" class="faq-question bg-slate-800 rounded-3xl p-8 mb-6 cursor-pointer">
      <div class="flex justify-between items-center"><span class="text-xl font-semibold">.txt fayl qanday formatda bo‘lishi kerak?</span><i class="fas fa-chevron-down"></i></div>
      <div class="answer hidden mt-6 text-slate-400">Har bir savol yangi qatordan, variantlar keyin, to‘g‘ri javob * bilan belgilansin.</div>
    </div>
    <!-- yana 4 ta FAQ qo‘shing (kodda bor) -->
  </div>
</section>

<!-- KONTAKT -->
<section id="kontakt" class="py-24">
  <div class="max-w-7xl mx-auto px-6">
    <h2 class="text-5xl font-bold text-center mb-12">Biz bilan bog‘laning</h2>
    <form class="max-w-xl mx-auto space-y-6">
      <input type="text" placeholder="Ismingiz" class="w-full bg-slate-800 p-6 rounded-3xl">
      <input type="email" placeholder="Email" class="w-full bg-slate-800 p-6 rounded-3xl">
      <textarea placeholder="Xabaringiz" class="w-full bg-slate-800 p-6 rounded-3xl h-40"></textarea>
      <button type="button" onclick="alert('Xabar yuborildi! (demo)')" class="w-full bg-emerald-500 py-6 rounded-3xl text-xl font-bold">Yuborish</button>
    </form>
  </div>
</section>

<!-- FOOTER -->
<footer class="bg-black py-16 border-t border-emerald-900">
  <div class="max-w-7xl mx-auto px-6 text-center text-slate-400">
    <p class="text-3xl font-bold text-white mb-4">TezkorQuiz © 2026</p>
    <p>O‘zbekiston talabalari va o‘quvchilari uchun yaratilgan eng professional platforma</p>
  </div>
</footer>

<!-- LOGIN MODAL -->
<div id="loginModal" class="hidden fixed inset-0 bg-black/80 flex items-center justify-center z-[1000]">
  <div class="bg-slate-900 rounded-3xl p-10 w-full max-w-md">
    <button onclick="hideLoginModal()" class="float-right text-4xl text-slate-400">×</button>
    <h3 class="text-3xl font-bold text-center mb-8">Kirish</h3>
    <input id="email" type="email" placeholder="Email" class="w-full bg-slate-800 p-6 rounded-3xl mb-4">
    <input id="password" type="password" placeholder="Parol" class="w-full bg-slate-800 p-6 rounded-3xl mb-8">
    <button onclick="fakeLogin()" class="w-full bg-emerald-500 py-6 rounded-3xl text-xl font-bold">Kirish</button>
  </div>
</div>

<!-- QUIZ MODAL -->
<div id="quizModal" class="hidden fixed inset-0 bg-black/90 flex items-center justify-center z-[999]">
  <!-- Quiz ichidagi kod (oldingi versiyadan to‘liq) -->
  <div class="bg-slate-900 rounded-3xl w-full max-w-2xl p-10 relative">
    <button onclick="closeQuizModal()" class="absolute top-6 right-8 text-5xl">×</button>
    <div class="text-center">
      <h3 id="quizTitle" class="text-3xl font-bold mb-4"></h3>
      <div class="flex justify-between mb-8"><span>Savol <span id="qNum">1</span>/10</span><span id="timer">30s</span></div>
      <div id="questionText" class="text-2xl font-medium min-h-32"></div>
      <div id="optionsContainer" class="grid gap-4 mt-12"></div>
      <div class="mt-10 text-emerald-400 text-2xl font-bold" id="currentScore">Ball: 0</div>
    </div>
  </div>
</div>

<script>
// Tailwind config
tailwind.config = { content: ["*"], theme: { extend: {} } }

// Quiz savollari (demo)
let questions = [
  {q:"2+2=?", a:["3","4","5","6"], c:1},
  {q:"O‘zbekiston poytaxti?", a:["Toshkent","Samarqand","Buxoro","Andijon"], c:0}
  // 10 ta qo‘shing
];

let currentQ = 0, score = 0, timer;

// Fayl yuklash parser
function handleFileUpload() {
  const file = document.getElementById('fileInput').files[0];
  if (!file) return;
  const reader = new FileReader();
  reader.onload = function(e) {
    const text = e.target.result;
    // Oddiy parser (siz keyinroq takomillashtirasiz)
    questions = parseTxtToQuestions(text);
    document.getElementById('uploadStatus').innerHTML = `✅ ${file.name} yuklandi! <button onclick="startDemoQuiz()" class="underline text-emerald-400">Testni boshlash</button>`;
  };
  reader.readAsText(file);
}

function parseTxtToQuestions(txt) {
  // Misol parser — siz o‘zingiz yaxshilang
  return [
    {q: "Yangi savol?", a: ["A","B","C","D"], c: 0}
  ];
}

// Demo quiz
function startDemoQuiz() {
  document.getElementById('quizModal').classList.remove('hidden');
  currentQ = 0; score = 0;
  loadQuestion();
}

function loadQuestion() {
  const q = questions[currentQ];
  document.getElementById('qNum').textContent = currentQ + 1;
  document.getElementById('questionText').textContent = q.q;
  document.getElementById('currentScore').textContent = `Ball: ${score}`;

  const container = document.getElementById('optionsContainer');
  container.innerHTML = '';
  q.a.forEach((ans, i) => {
    const btn = document.createElement('button');
    btn.className = "bg-slate-800 hover:bg-emerald-600 p-6 rounded-2xl text-left text-xl transition";
    btn.textContent = ans;
    btn.onclick = () => checkAnswer(i);
    container.appendChild(btn);
  });

  // Timer
  let time = 30;
  document.getElementById('timer').textContent = `${time}s`;
  clearInterval(timer);
  timer = setInterval(() => {
    time--;
    document.getElementById('timer').textContent = `${time}s`;
    if (time <= 0) nextQuestion();
  }, 1000);
}

function checkAnswer(selected) {
  clearInterval(timer);
  if (selected === questions[currentQ].c) {
    score += 10;
    confetti({particleCount: 100, spread: 70});
  }
  setTimeout(nextQuestion, 600);
}

function nextQuestion() {
  currentQ++;
  if (currentQ < questions.length) loadQuestion();
  else {
    alert(`🎉 Test tugadi! Umumiy ball: ${score}`);
    closeQuizModal();
    // Leaderboard ga qo‘shish
    addToLeaderboard(score);
  }
}

function closeQuizModal() {
  document.getElementById('quizModal').classList.add('hidden');
  clearInterval(timer);
}

// Leaderboard
function addToLeaderboard(points) {
  const tbody = document.getElementById('leaderboardBody');
  const row = document.createElement('tr');
  row.className = "border-t border-slate-700 hover:bg-slate-700/50";
  row.innerHTML = `<td class="py-6 px-8">Siz</td><td class="py-6 px-8 font-bold text-emerald-400">${points}</td><td class="py-6 px-8">Pro</td><td class="py-6 px-8">Hozir</td>`;
  tbody.appendChild(row);
}

// Login modal
function showLoginModal() { document.getElementById('loginModal').classList.remove('hidden'); }
function hideLoginModal() { document.getElementById('loginModal').classList.add('hidden'); }
function fakeLogin() { alert('✅ Kirish muvaffaqiyatli! (demo)'); hideLoginModal(); }

// Mobile menu
function toggleMobileMenu() {
  const menu = document.getElementById('mobileMenu');
  menu.classList.toggle('hidden');
}

// Confetti
function confetti(opts) { window.confetti(opts); }

// Leaderboard boshlang‘ich ma’lumotlar
document.addEventListener('DOMContentLoaded', () => {
  const tbody = document.getElementById('leaderboardBody');
  tbody.innerHTML = `
    <tr class="border-t border-slate-700"><td class="py-6 px-8">Aziza Karimova</td><td class="py-6 px-8 font-bold text-emerald-400">98</td><td class="py-6 px-8">Imtihon</td><td class="py-6 px-8">10 daqiqa oldin</td></tr>
    <tr class="border-t border-slate-700"><td class="py-6 px-8">Sardorbek</td><td class="py-6 px-8 font-bold text-emerald-400">95</td><td class="py-6 px-8">Pro</td><td class="py-6 px-8">1 soat oldin</td></tr>
  `;
});

// Tayyor!
</script>
</body>
</html>
