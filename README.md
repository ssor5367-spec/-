
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>أوهانا | OHANA</title>
<meta name="description" content="أوهانا، مساحة تجمع عشاق الروايات والقراءة والحكايات التي لا تُنسى.">

<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;800&family=Amiri:wght@400;700&display=swap" rel="stylesheet">

<style>
:root {
 --bg:#f4ecdf;
 --card:#fffaf2;
 --text:#30231d;
 --gold:#b58b50;
 --border:#dfd0bb;
 --muted:#8c7b6c;
}
[data-theme="dark"] {
 --bg:#191715;
 --card:#29231f;
 --text:#f5eadd;
 --gold:#d6ad70;
 --border:#493b30;
 --muted:#b3a394;
}
* {box-sizing:border-box;margin:0;padding:0}
html {scroll-behavior:smooth}
body {
 background:var(--bg);
 color:var(--text);
 font-family:'Cairo',sans-serif;
 transition:.3s;
}
header {
 background:var(--card);
 border-bottom:1px solid var(--border);
 padding:15px 6%;
 display:flex;
 justify-content:space-between;
 align-items:center;
 flex-wrap:wrap;
 gap:15px;
 position:sticky;
 top:0;
 z-index:10;
}
.logo {font-size:26px;font-weight:800;color:var(--gold)}
nav {display:flex;gap:18px;flex-wrap:wrap}
nav a {text-decoration:none;color:var(--text);font-size:14px}
nav a:hover {color:var(--gold)}
button {
 cursor:pointer;
 border:0;
 border-radius:7px;
 padding:10px 17px;
 background:var(--gold);
 color:white;
 font-family:'Cairo',sans-serif;
 font-weight:bold;
}
button:hover {opacity:.85}
.hero {
 min-height:420px;
 padding:50px 20px;
 display:flex;
 flex-direction:column;
 align-items:center;
 justify-content:center;
 text-align:center;
 background:linear-gradient(135deg,var(--card),var(--bg));
 border-bottom:1px solid var(--border);
}
.hero h1 {
 font-family:'Amiri',serif;
 font-size:55px;
 color:var(--gold);
}
.hero .quote {
 font-family:'Amiri',serif;
 font-size:30px;
 line-height:1.9;
 margin:15px 0;
}
.hero .quote strong {color:var(--gold)}
.hero p {color:var(--muted);font-size:14px}
.hero button {margin-top:25px}
.container {
 max-width:1150px;
 margin:auto;
 padding:40px 20px;
}
.section-title {
 font-family:'Amiri',serif;
 font-size:32px;
 color:var(--gold);
 margin-bottom:7px;
}
.desc {color:var(--muted);font-size:14px;margin-bottom:20px}
.search {
 width:100%;
 padding:14px;
 background:var(--card);
 color:var(--text);
 border:1px solid var(--border);
 border-radius:8px;
 font-family:'Cairo',sans-serif;
 margin:15px 0;
}
.categories {
 display:flex;
 gap:9px;
 flex-wrap:wrap;
 margin:10px 0 25px;
}
.categories button {
 background:var(--card);
 color:var(--text);
 border:1px solid var(--border);
}
.categories button.active {
 background:var(--gold);
 color:white;
}
.books {
 display:grid;
 grid-template-columns:repeat(auto-fit,minmax(210px,1fr));
 gap:20px;
}
.book {
 background:var(--card);
 border:1px solid var(--border);
 border-radius:12px;
 overflow:hidden;
 transition:.2s;
}
.book:hover {transform:translateY(-4px)}
.cover {
 height:190px;
 display:flex;
 align-items:center;
 justify-content:center;
 text-align:center;
 padding:15px;
 color:#f8e9d0;
 background:linear-gradient(145deg,#392820,#99704a);
 font-family:'Amiri',serif;
 font-size:29px;
}
.book-info {padding:16px}
.book-info h3 {color:var(--gold);margin-bottom:5px}
.book-info p {font-size:13px;color:var(--muted);margin-bottom:12px}
.book-info button {width:100%}
.reader {
 display:none;
 background:var(--card);
 border:1px solid var(--border);
 padding:22px;
 border-radius:12px;
 margin-top:25px;
}
.reader h3 {color:var(--gold);margin-bottom:12px}
.reader textarea {
 width:100%;
 min-height:300px;
 padding:15px;
 background:var(--bg);
 color:var(--text);
 border:1px solid var(--border);
 border-radius:8px;
 font-family:'Amiri',serif;
 font-size:20px;
 line-height:2;
}
.reader input {
 width:100%;
 padding:12px;
 margin-bottom:12px;
 background:var(--bg);
 color:var(--text);
 border:1px solid var(--border);
 border-radius:7px;
 font-family:'Cairo',sans-serif;
}
.about {
 background:var(--card);
 border:1px solid var(--border);
 padding:25px;
 border-radius:12px;
 line-height:2.2;
}
.empty {
 display:none;
 color:var(--muted);
 padding:20px;
 text-align:center;
}
footer {
 text-align:center;
 padding:28px 15px;
 color:var(--gold);
 border-top:1px solid var(--border);
 font-family:'Amiri',serif;
 font-size:18px;
}
@media(max-width:650px) {
 header {justify-content:center}
 nav {justify-content:center}
 .hero h1 {font-size:43px}
 .hero .quote {font-size:23px}
}
</style>
</head>

<body>

<header>
 <div class="logo">أوهانا | OHANA</div>
 <nav>
  <a href="#home">الرئيسية</a>
  <a href="#library">مكتبة الروايات</a>
  <a href="#reader">القراءة</a>
  <a href="#about">عن أوهانا</a>
 </nav>
 <button onclick="toggleTheme()">🌙 الوضع الليلي</button>
</header>

<section class="hero" id="home">
 <h1>أهلاً بك في أوهانا</h1>
 <div class="quote">
  أوهانا يعني العيلة..<br>
  <strong>والعيلة معناها إن محدش فيها بيتنسي.</strong>
 </div>
 <p>هنا تبدأ الحكايات، وهنا تجد كل رواية مكانها.</p>
 <button onclick="document.getElementById('library').scrollIntoView()">
   عالم الروايات
 </button>
</section>

<main>

<section class="container" id="library">
 <h2 class="section-title">📚 مكتبة أوهانا</h2>
 <p class="desc">اختر روايتك القادمة وانطلق في عالم من الحكايات.</p>

 <input class="search" id="search" type="search"
 placeholder="ابحث عن رواية..." oninput="filterBooks()">

 <div class="categories">
  <button class="active" onclick="setCategory('الكل',this)">الكل</button>
  <button onclick="setCategory('خيال',this)">خيال</button>
  <button onclick="setCategory('غموض',this)">غموض</button>
  <button onclick="setCategory('رعب',this)">رعب</button>
  <button onclick="setCategory('دراما',this)">دراما</button>
  <button onclick="setCategory('مغامرة',this)">مغامرة</button>
 </div>

 <div class="books" id="books">

  <article class="book" data-category="خيال" data-name="أرض زيكولا">
   <div class="cover">أرض زيكولا</div>
   <div class="book-info">
    <h3>أرض زيكولا</h3>
    <p>خيال ومغامرة</p>
    <button onclick="openReader('أرض زيكولا')">استكشف الرواية</button>
   </div>
  </article>

  <article class="book" data-category="غموض" data-name="قواعد جارتين">
   <div class="cover">قواعد جارتين</div>
   <div class="book-info">
    <h3>قواعد جارتين</h3>
    <p>غموض وخيال</p>
    <button onclick="openReader('قواعد جارتين')">استكشف الرواية</button>
   </div>
  </article>

  <article class="book" data-category="رعب" data-name="نبيذ الغربان">
   <div class="cover">نبيذ الغربان</div>
   <div class="book-info">
    <h3>نبيذ الغربان</h3>
    <p>رعب وغموض</p>
    <button onclick="openReader('نبيذ الغربان')">استكشف الرواية</button>
   </div>
  </article>

  <article class="book" data-category="دراما" data-name="صوت في الإذاعة">
   <div class="cover">صوت في الإذاعة</div>
   <div class="book-info">
    <h3>صوت في الإذاعة</h3>
    <p>غموض ودراما</p>
    <button onclick="openReader('صوت في الإذاعة')">استكشف الرواية</button>
   </div>
  </article>

 </div>
 <div class="empty" id="empty">لا توجد روايات مطابقة لبحثك.</div>

 <div class="reader" id="reader">
  <h3 id="readerTitle">عنوان الرواية</h3>
  <p class="desc">مساحة قراءة الرواية</p>
  <input id="chapterName" placeholder="عنوان الفصل">
  <textarea id="chapterText" placeholder="يمكنك إضافة نص الرواية هنا..."></textarea>
  <br><br>
  <button onclick="saveReading()">💾 حفظ النص</button>
  <button onclick="downloadReading()">📥 تحميل النص</button>
  <button onclick="closeReader()">إغلاق</button>
 </div>
</section>

<section class="container" id="about">
 <h2 class="section-title">عن أوهانا</h2>
 <div class="about">
  <p>
   أوهانا ليست مجرد مكتبة للروايات، بل مساحة تجمع محبي القراءة
   وعشاق الحكايات والشخصيات التي تظل حية في ذاكرتنا.
  </p>
  <p>
   هنا لكل قارئ عالم مختلف عما يعيشه في واقعه.
  </p>
  <p><strong>أوهانا يعني العيلة.. والعيلة معناها إن محدش فيها بيتنسي.</strong></p>
 </div>
</section>

</main>

<footer>
 أوهانا | OHANA
 <br>
 أوهانا يعني العيلة.. والعيلة معناها إن محدش فيها بيتنسي.
</footer>

<script>
let currentCategory = "الكل";
let currentNovel = "";

function toggleTheme() {
 const dark = document.body.dataset.theme !== "dark";
 document.body.dataset.theme = dark ? "dark" : "light";
 localStorage.setItem("ohana_theme",dark ? "dark" : "light");
}

function setCategory(category,button) {
 currentCategory = category;
 document.querySelectorAll(".categories button").forEach(b=>{
  b.classList.remove("active");
 });
 button.classList.add("active");
 filterBooks();
}

function filterBooks() {
 const query = document.getElementById("search").value.trim().toLowerCase();
 const books = document.querySelectorAll(".book");
 let count = 0;

 books.forEach(book=>{
  const name = book.dataset.name.toLowerCase();
  const category = book.dataset.category;
  const matchName = name.includes(query);
  const matchCategory = currentCategory === "الكل" || category === currentCategory;
  book.style.display = matchName && matchCategory ? "" : "none";
  if(matchName && matchCategory) count++;
 });

 document.getElementById("empty").style.display = count ? "none" : "block";
}

function openReader(name) {
 currentNovel = name;
 document.getElementById("readerTitle").textContent = name;
 document.getElementById("chapterName").value =
  localStorage.getItem("chapter_" + name) || "";
 document.getElementById("chapterText").value =
  localStorage.getItem("text_" + name) || "";
 document.getElementById("reader").style.display = "block";
 document.getElementById("reader").scrollIntoView({behavior:"smooth"});
}

function saveReading() {
 if(!currentNovel) return;
 localStorage.setItem("chapter_" + currentNovel,
  document.getElementById("chapterName").value);
 localStorage.setItem("text_" + currentNovel,
  document.getElementById("chapterText").value);
 alert("تم حفظ النص على هذا الجهاز بنجاح.");
}

function downloadReading() {
 const chapter = document.getElementById("chapterName").value;
 const text = document.getElementById("chapterText").value;
 const content = currentNovel + "\n" + chapter + "\n\n" + text;
 const blob = new Blob(["\ufeff" + content],{type:"text/plain;charset=utf-8"});
 const url = URL.createObjectURL(blob);
 const a = document.createElement("a");
 a.href = url;
 a.download = (currentNovel || "رواية") + ".txt";
 a.click();
 URL.revokeObjectURL(url);
}

function closeReader() {
 document.getElementById("reader").style.display = "none";
}

window.onload = function() {
 if(localStorage.getItem("ohana_theme") === "dark") {
  document.body.dataset.theme = "dark";
 }
};
</script>

</body>
</html>
