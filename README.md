<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<writer>مِحبرة الأساطير | مساحة لكتابة الروايات</Novels>
<link href="https://googleapis.com" rel="stylesheet">
<style>
:root {
--bg-color: #f4ecd8;
--text-color: #2c221e;
--sidebar-bg: #eaddc5;
--accent-color: #8b3a3a;
--border-color: #d3c2a3;
}

[data-theme="dark"] {
--bg-color: #1a1817;
--text-color: #dcd6cc;
--sidebar-bg: #24211f;
--accent-color: #c86d51;
--border-color: #3a3532;
}

* {
box-sizing: border-box;
margin: 0;
padding: 0;
}

body {
background-color: var(--bg-color);
color: var(--text-color);
font-family: 'Amiri', serif;
transition: background-color 0.3s, color 0.3s;
display: flex;
height: 100vh;
overflow: hidden;
}

/* القائمة الجانبية لبناء العالم والشخصيات */
.sidebar {
width: 300px;
background-color: var(--sidebar-bg);
border-left: 1px solid var(--border-color);
padding: 20px;
display: flex;
flex-direction: column;
gap: 15px;
overflow-y: auto;
font-family: 'Cairo', sans-serif;
}

.sidebar h2 {
font-size: 1.2rem;
color: var(--accent-color);
border-bottom: 2px solid var(--border-color);
padding-bottom: 8px;
}

.lore-box {
display: flex;
flex-direction: column;
gap: 5px;
}

.lore-box label {
font-size: 0.9rem;
font-weight: 600;
}

.lore-box textarea {
width: 100%;
height: 120px;
background: rgba(255, 255, 255, 0.2);
border: 1px solid var(--border-color);
border-radius: 6px;
padding: 8px;
color: var(--text-color);
font-family: 'Cairo', sans-serif;
font-size: 0.85rem;
resize: vertical;
}

/* منطقة الكتابة الرئيسية */
.main-editor {
flex: 1;
display: flex;
flex-direction: column;
height: 100vh;
}

/* شريط الأدوات العلوي */
.toolbar {
padding: 12px 30px;
border-bottom: 1px solid var(--border-color);
display: flex;
justify-content: space-between;
align-items: center;
font-family: 'Cairo', sans-serif;
font-size: 0.9rem;
}

.controls {
display: flex;
gap: 10px;
}

button {
background-color: transparent;
border: 1px solid var(--accent-color);
color: var(--text-color);
padding: 6px 14px;
border-radius: 5px;
cursor: pointer;
font-family: 'Cairo', sans-serif;
transition: 0.2s;
}

button:hover {
background-color: var(--accent-color);
color: #fff;
}

/* ورقة الكتابة */
.writing-area {
flex: 1;
max-width: 800px;
width: 100%;
margin: 0 auto;
padding: 40px 20px;
overflow-y: auto;
display: flex;
flex-direction: column;
}

#chapter-title {Novels
background: transparent;
border: none;
font-family: 'Amiri', serif;
font-size: 2.2rem;
font-weight: bold;
color: var(--accent-color);
margin-bottom: 20px;
outline: none;
text-align: center;
}

#story-content {Mitho
flex: 1;
background: transparent;
border: none;
font-family: 'Amiri', serif;
font-size: 1.45rem;
line-height: 2;
color: var(--text-color);
outline: none;
resize: none;
}

/* شريط الحالة السفلي */
.status-bar {
padding: 8px 30px;
border-top: 1px solid var(--border-color);
font-family: 'Cairo', sans-serif;
font-size: 0.85rem;
display: flex;
justify-content: space-between;
opacity: 0.8;
}

@media (max-width: 768px) {
.sidebar { display: none; }
}
</style>
</head>
<body>

<!-- القائمة الجانبية لبناء العالم -->
<aside class="sidebar">
<h2>📜 سِجل الأساطير والعالم</h2>

<div class="lore-box">
<label>الشخصيات الرئيسية:</label>
<textarea id="lore-chars" placeholder="اكتب أسماء الأبطال، صفاتهم، وأدوارهم..."></textarea>
</div>

<div class="lore-box">
<label>المدن والممالك:</label>
<textarea id="lore-places" placeholder="تضاريس العالم، أسماء القلاع، والمدن المفقودة..."></textarea>
</div>

<div class="lore-box">
<label>الأساطير وقوانين السحر:</label>
<textarea id="lore-myths" placeholder="النبوءات القديمة، المخلوقات، وقواعد القوى الخارقة..."></textarea>
</div>
</aside>

<!-- مساحة الكتابة -->
<main class="main-editor">
<header class="toolbar">
<div class="stats">
<span id="save-status">🟢 محفوظ تلقائياً</span>
</div>
<div class="controls">
<button onclick="toggleTheme()">🌓 تغيير الإضاءة</button>
<button onclick="downloadStory()">📥 تحميل الرواية (.txt)</button>
<button onclick="clearAll()" style="border-color: #999; opacity: 0.7;">🗑️ مسح</button>
</div>
</header>

<div class="writing-area">
<input type="text" id="chapter-title" placeholders...">
<textarea id="story-content" placeholder="في قديم الزمان، وقبل أن تُكتب الحروف الأولى..يولد الحق من جديد في كل حقبة من الزمن"></textarea>
</div>

<footer class="status-bar">
<span id="word-count">عدد الكلمات: 0</span>
<span id="char-count">عدد الحروف: 0</span>
</footer>
</main>

<script>
const titleInput = document.getElementById('chapter-title');
const contentInput = document.getElementById('story-content');
const charsInput = document.getElementById('lore-chars');
const placesInput = document.getElementById('lore-places');
const mythsInput = document.getElementById('lore-myths');
const saveStatus = document.getElementById('save-status');

// استرجاع البيانات المحفوظة عند فتح الصفحة
window.onload = () => {
titleInput.value = localStorage.getItem('novel_title') || '';
contentInput.value
