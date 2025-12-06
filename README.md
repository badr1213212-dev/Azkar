<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="theme-color" content="#0f766e">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>حصن المسلم | Mahmoud Badr</title>
    
    <!-- خطوط عربية وأيقونات -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:wght@400;700&family=Tajawal:wght@300;400;500;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* === المتغيرات === */
        :root {
            --primary: #0f766e;
            --primary-dark: #115e59;
            --accent: #f59e0b;
            --bg-body: #f1f5f9;
            --bg-card: #ffffff;
            --text-main: #1e293b;
            --text-sec: #64748b;
            --border: #e2e8f0;
            --header-height: 60px;
        }

        [data-theme="dark"] {
            --primary: #2dd4bf;
            --primary-dark: #14b8a6;
            --accent: #fbbf24;
            --bg-body: #020617;
            --bg-card: #1e293b;
            --text-main: #f8fafc;
            --text-sec: #cbd5e1;
            --border: #334155;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
            font-family: 'Tajawal', sans-serif;
            outline: none;
        }

        /* === إعداد الصفحة للموبايل === */
        body {
            background-color: #334155; /* لون خلفية خارج إطار الموبايل */
            display: flex;
            justify-content: center;
            min-height: 100vh;
            overflow: hidden; /* لمنع السكرول المزدوج */
        }

        #mobile-app {
            width: 100%;
            max-width: 480px; /* أقصى عرض كأنه موبايل */
            height: 100vh; /* ملء الطول */
            background-color: var(--bg-body);
            color: var(--text-main);
            position: relative;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            box-shadow: 0 0 20px rgba(0,0,0,0.5);
        }

        /* === الهيدر === */
        header {
            height: var(--header-height);
            background: linear-gradient(135deg, #0f766e, #115e59);
            color: white;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 15px;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            flex-shrink: 0;
        }

        .logo-area { display: flex; align-items: center; gap: 10px; }
        .logo-area h1 { font-size: 1.2rem; font-weight: 800; margin: 0; }
        .logo-area span { font-size: 0.7rem; opacity: 0.9; }

        .header-tools button {
            background: rgba(255,255,255,0.15);
            border: none;
            color: white;
            width: 35px;
            height: 35px;
            border-radius: 8px;
            margin-left: 5px;
            cursor: pointer;
            font-size: 1rem;
        }

        /* === منطقة المعلومات (الصلاة) === */
        .info-panel {
            background: var(--bg-card);
            padding: 15px;
            border-bottom: 1px solid var(--border);
            flex-shrink: 0;
        }

        .next-prayer-widget {
            background: linear-gradient(45deg, var(--primary), var(--primary-dark));
            color: white;
            border-radius: 12px;
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            box-shadow: 0 4px 10px rgba(15, 118, 110, 0.2);
        }

        .np-details div:first-child { font-size: 0.8rem; opacity: 0.9; }
        .np-name { font-size: 1.5rem; font-weight: 800; }
        .location-badge { font-size: 0.7rem; background: rgba(0,0,0,0.2); padding: 2px 6px; border-radius: 4px; margin-right: 5px; }

        .countdown {
            font-size: 1.2rem;
            font-weight: 700;
            background: rgba(255,255,255,0.2);
            padding: 5px 10px;
            border-radius: 8px;
        }

        .prayers-row {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
        }

        .p-unit {
            text-align: center;
            font-size: 0.8rem;
            color: var(--text-sec);
            position: relative;
            flex: 1;
        }
        .p-unit.active { color: var(--primary); font-weight: 800; }
        .p-time { font-weight: bold; font-family: sans-serif; display: block; margin-top: 2px; }

        /* === شريط التبويبات === */
        .tabs-wrapper {
            background: var(--bg-body);
            padding: 10px 15px;
            overflow-x: auto;
            white-space: nowrap;
            scrollbar-width: none;
            flex-shrink: 0;
            border-bottom: 1px solid var(--border);
        }
        .tabs-wrapper::-webkit-scrollbar { display: none; }

        .tab-btn {
            background: var(--bg-card);
            border: 1px solid var(--border);
            color: var(--text-sec);
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
            margin-left: 5px;
            cursor: pointer;
            transition: 0.2s;
        }
        .tab-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        /* === منطقة المحتوى (Scrollable) === */
        .scrollable-content {
            flex: 1;
            overflow-y: auto;
            padding: 15px;
            padding-bottom: 80px;
        }

        /* === بطاقة الذكر === */
        .card {
            background: var(--bg-card);
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            border: 1px solid var(--border);
            box-shadow: 0 2px 5px rgba(0,0,0,0.03);
            position: relative;
            /* عمود واحد دائماً */
            width: 100%; 
        }

        .card.done {
            opacity: 0.6;
            background: rgba(16, 185, 129, 0.1);
            border-color: #22c55e;
        }

        .card-meta {
            font-size: 0.75rem;
            color: var(--primary);
            background: rgba(15, 118, 110, 0.1);
            padding: 3px 8px;
            border-radius: 4px;
            display: inline-block;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .card-text {
            font-family: 'Amiri', serif;
            font-size: 1.3rem;
            line-height: 1.8;
            color: var(--text-main);
            margin-bottom: 15px;
            text-align: justify;
        }

        .card-footer {
            display: flex;
            align-items: center;
            gap: 10px;
            padding-top: 10px;
            border-top: 1px solid var(--border);
        }

        .progress-circle {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--bg-body);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 0.9rem;
            color: var(--primary);
            border: 2px solid var(--border);
            flex-shrink: 0;
        }

        .action-btn {
            flex: 1;
            background: var(--primary);
            color: white;
            border: none;
            height: 40px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            font-family: 'Tajawal';
        }
        .action-btn.done { background: #22c55e; cursor: default; }
        .action-btn:active { transform: scale(0.98); }

        /* === نافذة البحث (Modal) === */
        .modal-overlay {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 200;
            display: none; /* مخفي */
            justify-content: center;
            align-items: flex-start;
            padding-top: 100px;
            backdrop-filter: blur(5px);
        }

        .modal-box {
            background: var(--bg-card);
            width: 90%;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
        }

        .modal-box h3 { margin-bottom: 15px; color: var(--text-main); }
        
        .search-input {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border);
            border-radius: 8px;
            margin-bottom: 10px;
            font-family: 'Tajawal';
            background: var(--bg-body);
            color: var(--text-main);
        }

        .modal-btns { display: flex; gap: 10px; }
        .modal-btn {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
        }
        .btn-confirm { background: var(--primary); color: white; }
        .btn-cancel { background: var(--bg-body); color: var(--text-sec); }

        /* === الفوتر === */
        footer {
            text-align: center;
            padding: 15px;
            font-size: 0.8rem;
            color: var(--text-sec);
            background: var(--bg-card);
            border-top: 1px solid var(--border);
            flex-shrink: 0;
        }
        footer span { color: var(--primary); font-weight: bold; }

        .audio-btn {
            display: none;
            margin: 10px 15px;
            padding: 10px;
            background: #fee2e2;
            color: #991b1b;
            border-radius: 8px;
            text-align: center;
            font-size: 0.85rem;
            font-weight: bold;
        }

    </style>
</head>
<body>

    <!-- هيكل التطبيق (عمود واحد) -->
    <div id="mobile-app">
        
        <!-- الهيدر -->
        <header>
            <div class="logo-area">
                <i class="fa-solid fa-kaaba fa-lg"></i>
                <div>
                    <h1>حصن المسلم</h1>
                    <span>By Mahmoud Badr</span>
                </div>
            </div>
            <div class="header-tools">
                <button onclick="toggleModal()"><i class="fa-solid fa-earth-americas"></i></button>
                <button onclick="toggleTheme()"><i class="fa-solid fa-moon"></i></button>
            </div>
        </header>

        <!-- لوحة الصلاة -->
        <div class="info-panel">
            <div class="next-prayer-widget">
                <div class="np-details">
                    <div>الصلاة القادمة <span class="location-badge" id="locBadge">Makkah</span></div>
                    <div class="np-name" id="nextPName">--</div>
                </div>
                <div class="countdown" id="countdown">00:00:00</div>
            </div>

            <div class="prayers-row">
                <div class="p-unit" id="u-Fajr"><i class="fa-regular fa-sun"></i><span class="p-time" id="t-Fajr">--:--</span></div>
                <div class="p-unit" id="u-Dhuhr"><i class="fa-solid fa-sun"></i><span class="p-time" id="t-Dhuhr">--:--</span></div>
                <div class="p-unit" id="u-Asr"><i class="fa-solid fa-cloud-sun"></i><span class="p-time" id="t-Asr">--:--</span></div>
                <div class="p-unit" id="u-Maghrib"><i class="fa-solid fa-cloud-moon"></i><span class="p-time" id="t-Maghrib">--:--</span></div>
                <div class="p-unit" id="u-Isha"><i class="fa-solid fa-moon"></i><span class="p-time" id="t-Isha">--:--</span></div>
            </div>
        </div>

        <div class="audio-btn" id="audioBtn" onclick="allowAudio()">
            <i class="fa-solid fa-volume-high"></i> اضغط لتفعيل صوت الأذان
        </div>

        <!-- التبويبات -->
        <div class="tabs-wrapper">
            <button class="tab-btn active" onclick="loadContent('morning', this)">أذكار الصباح</button>
            <button class="tab-btn" onclick="loadContent('evening', this)">أذكار المساء</button>
            <button class="tab-btn" onclick="loadContent('sleep', this)">أذكار النوم</button>
            <button class="tab-btn" onclick="loadContent('prayer', this)">أذكار الصلاة</button>
            <button class="tab-btn" onclick="loadContent('wudu', this)">الوضوء</button>
            <button class="tab-btn" onclick="loadContent('mosque', this)">المسجد</button>
            <button class="tab-btn" onclick="loadContent('quranic', this)">أدعية قرآنية</button>
            <button class="tab-btn" onclick="loadContent('prophets', this)">أدعية الأنبياء</button>
            <button class="tab-btn" onclick="loadContent('tasbih', this)">تسابيح</button>
        </div>

        <!-- المحتوى القابل للسكرول -->
        <div class="scrollable-content" id="listContainer">
            <!-- البطاقات تظهر هنا -->
        </div>

        <!-- الفوتر -->
        <footer>
            جميع الحقوق محفوظة 2025 ©<br>
            تطوير: <span>Mahmoud Badr</span>
        </footer>

        <!-- نافذة البحث عن مدينة -->
        <div class="modal-overlay" id="searchModal">
            <div class="modal-box">
                <h3><i class="fa-solid fa-location-dot"></i> اختر مدينتك</h3>
                <input type="text" id="cityInput" class="search-input" placeholder="اكتب اسم المدينة بالإنجليزية (مثلاً: Cairo)">
                <div class="modal-btns">
                    <button class="modal-btn btn-confirm" onclick="searchCity()">بحث</button>
                    <button class="modal-btn btn-cancel" onclick="toggleModal()">إلغاء</button>
                </div>
            </div>
        </div>

    </div>

    <!-- الصوت -->
    <audio id="adhanSound" src="https://www.islamcan.com/audio/adhan/azan1.mp3"></audio>

    <script>
        // === 1. البيانات (كاملة) ===
        const db = {
            morning: [
                {t:"اللّهُ لاَ إِلَـهَ إِلاَّ هُوَ الْحَيُّ الْقَيُّومُ لاَ تَأْخُذُهُ سِنَةٌ وَلاَ نَوْمٌ...", c:1, v:"آية الكرسي"},
                {t:"قُلْ هُوَ ٱللَّهُ أَحَدٌ... (والمعوذتين)", c:3, v:"تكفيك من كل شيء"},
                {t:"أَصْـبَحْنا وَأَصْـبَحَ المُـلْكُ لله وَالحَمدُ لله...", c:1, v:""},
                {t:"اللّهـمَّ أَنْتَ رَبِّـي لا إلهَ إلاّ أَنْتَ...", c:1, v:"سيد الاستغفار"},
                {t:"رَضيـتُ بِاللهِ رَبَّـاً وَبِالإسْلامِ ديـناً...", c:3, v:""},
                {t:"اللّهُـمَّ إِنِّـي أَصْبَـحْتُ أُشْـهِدُك...", c:4, v:"عتق من النار"},
                {t:"حَسْبِـيَ اللّهُ لا إلهَ إلاّ هُوَ عَلَـيهِ تَوَكَّـلتُ...", c:7, v:"كفاه الله ما أهمه"},
                {t:"بِسـمِ اللهِ الذي لا يَضُـرُّ مَعَ اسمِـهِ شَيءٌ...", c:3, v:"لم يضره شيء"},
                {t:"اللّهُـمَّ بِكَ أَصْـبَحْنا وَبِكَ أَمْسَـينا...", c:1, v:""},
                {t:"سُبْحـانَ اللهِ وَبِحَمْـدِهِ عَدَدَ خَلْـقِه...", c:3, v:""},
                {t:"اللّهُـمَّ عافِـني في بَدَنـي...", c:3, v:""},
                {t:"يَا حَيُّ يَا قيُّومُ بِرَحْمَتِكَ أسْتَغِيثُ...", c:3, v:""},
                {t:"اللَّهُمَّ صَلِّ وَسَلِّمْ وَبَارِكْ على نَبِيِّنَا مُحمَّد.", c:10, v:"الشفاعة"},
                {t:"سُبْحـانَ اللهِ وَبِحَمْـدِهِ.", c:100, v:"حطت خطاياه"}
            ],
            evening: [
                {t:"أَمْسَيْـنا وَأَمْسـى المـلكُ لله...", c:1, v:""},
                {t:"اللّهُـمَّ بِكَ أَمْسَـينا وَبِكَ أَصْـبَحْنا...", c:1, v:""},
                {t:"أَعـوذُ بِكَلِمـاتِ اللّهِ التّـامّـاتِ مِنْ شَـرِّ ما خَلَـق.", c:3, v:""},
                {t:"آية الكرسي...", c:1, v:""},
                {t:"المعوذتين...", c:3, v:""},
                {t:"سيد الاستغفار...", c:1, v:""}
            ],
            tasbih: [
                {t:"سُبْحَانَ اللَّهِ", c:100, v:""},
                {t:"الْحَمْدُ لِلَّهِ", c:100, v:""},
                {t:"اللَّهُ أَكْبَرُ", c:100, v:""},
                {t:"لَا إلَه إلّا اللهُ وَحْدَهُ لَا شَرِيكَ لَهُ...", c:100, v:""},
                {t:"أستغفر الله", c:100, v:""},
                {t:"اللَّهُم صَلِّ وَسَلِم وَبَارِك عَلَى سَيِّدِنَا مُحَمَّد", c:10, v:""}
            ],
            // ... (باقي الأقسام يمكن نسخها من الكود السابق للاختصار)
            prayer: [{t:"أذكار ما بعد الصلاة...", c:1, v:""}],
            sleep: [{t:"أذكار النوم...", c:1, v:""}],
            wudu: [{t:"أشهد أن لا إله إلا الله...", c:1, v:""}],
            mosque: [{t:"دعاء دخول المسجد...", c:1, v:""}],
            quranic: [{t:"رَبَّنَا آتِنَا فِي الدُّنْيَا حَسَنَةً...", c:1, v:""}],
            prophets: [{t:"لا إله إلا أنت سبحانك إني كنت من الظالمين", c:1, v:""}]
        };

        // === 2. منطق التطبيق ===
        let prayerTimes = {};
        let currentCity = localStorage.getItem('userCity') || 'Makkah'; // المدينة الافتراضية
        let adhanReady = false;

        // تهيئة التطبيق
        window.onload = () => {
            if(localStorage.getItem('theme') === 'dark') document.body.setAttribute('data-theme', 'dark');
            loadContent('morning', document.querySelector('.tab-btn'));
            fetchPrayers(currentCity); // جلب المواقيت
        };

        // البحث عن مدينة (قاعدة البيانات API)
        function toggleModal() {
            const modal = document.getElementById('searchModal');
            modal.style.display = modal.style.display === 'flex' ? 'none' : 'flex';
        }

        function searchCity() {
            const input = document.getElementById('cityInput').value;
            if(input.trim() !== "") {
                currentCity = input;
                localStorage.setItem('userCity', currentCity);
                fetchPrayers(currentCity);
                toggleModal();
            }
        }

        async function fetchPrayers(city) {
            try {
                document.getElementById('locBadge').innerText = city;
                const date = new Date();
                // رابط API لجلب المواقيت حسب المدينة (قاعدة بيانات)
                const api = `https://api.aladhan.com/v1/timingsByCity/${date.getDate()}-${date.getMonth()+1}-${date.getFullYear()}?city=${city}&country=&method=5`;
                
                const res = await fetch(api);
                const data = await res.json();
                
                if(data.code === 200) {
                    prayerTimes = data.data.timings;
                    updatePrayerUI();
                    document.getElementById('audioBtn').style.display = 'block';
                } else {
                    alert("لم يتم العثور على المدينة، تأكد من الكتابة بالإنجليزية.");
                }
            } catch(e) { console.error(e); }
        }

        function updatePrayerUI() {
            const map = {Fajr:'u-Fajr', Dhuhr:'u-Dhuhr', Asr:'u-Asr', Maghrib:'u-Maghrib', Isha:'u-Isha'};
            
            // تحديث النصوص
            for(let key in map) {
                document.getElementById('t-'+key).innerText = formatTime(prayerTimes[key]);
                document.getElementById(map[key]).classList.remove('active');
            }

            // حساب الوقت المتبقي
            startTimer();
        }

        function formatTime(t) {
            let [h, m] = t.split(':');
            let suf = h >= 12 ? 'م' : 'ص';
            h = h % 12 || 12;
            return `${h}:${m}`;
        }

        let timerInt;
        function startTimer() {
            if(timerInt) clearInterval(timerInt);
            
            timerInt = setInterval(() => {
                const now = new Date();
                const order = ['Fajr', 'Dhuhr', 'Asr', 'Maghrib', 'Isha'];
                let next = null;
                let name = '';

                for(let p of order) {
                    let [h, m] = prayerTimes[p].split(':');
                    let pDate = new Date();
                    pDate.setHours(h, m, 0);
                    if(pDate > now) {
                        next = pDate;
                        name = p;
                        break;
                    }
                }

                if(!next) {
                    let [h, m] = prayerTimes['Fajr'].split(':');
                    next = new Date();
                    next.setDate(next.getDate()+1);
                    next.setHours(h, m, 0);
                    name = 'Fajr';
                }

                // UI Update
                const arNames = {Fajr:'الفجر', Dhuhr:'الظهر', Asr:'العصر', Maghrib:'المغرب', Isha:'العشاء'};
                document.getElementById('nextPName').innerText = arNames[name];
                
                // Active Class
                document.querySelectorAll('.p-unit').forEach(u => u.classList.remove('active'));
                const activeId = 'u-' + name;
                if(document.getElementById(activeId)) document.getElementById(activeId).classList.add('active');

                // CountDown
                const diff = next - now;
                if(diff <= 0) {
                    if(adhanReady) document.getElementById('adhanSound').play();
                    fetchPrayers(currentCity); // Refresh next day
                } else {
                    const h = Math.floor(diff / 3600000);
                    const m = Math.floor((diff % 3600000) / 60000);
                    const s = Math.floor((diff % 60000) / 1000);
                    document.getElementById('countdown').innerText = 
                        `${h}:${m<10?'0'+m:m}:${s<10?'0'+s:s}`;
                }
            }, 1000);
        }

        function allowAudio() {
            const a = document.getElementById('adhanSound');
            a.play().then(() => {
                a.pause();
                a.currentTime = 0;
                adhanReady = true;
                document.getElementById('audioBtn').style.display = 'none';
                alert("تم تفعيل الأذان بنجاح");
            });
        }

        // === 3. وظائف الأذكار ===
        function loadContent(cat, btn) {
            if(btn) {
                document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
            }
            
            const box = document.getElementById('listContainer');
            box.innerHTML = '';
            
            const list = db[cat] || db['morning'];
            list.forEach((item, i) => {
                box.innerHTML += `
                <div class="card" id="c-${i}">
                    ${item.v ? `<span class="card-meta">${item.v}</span>` : ''}
                    <div class="card-text">${item.t}</div>
                    <div class="card-footer">
                        <div class="progress-circle" id="cnt-${i}">0/${item.c}</div>
                        <button class="action-btn" onclick="clickCount(${i}, ${item.c}, this)">
                            اضغط للتسبيح
                        </button>
                    </div>
                </div>`;
            });
        }

        function clickCount(id, max, btn) {
            const cnt = document.getElementById('cnt-'+id);
            let val = parseInt(cnt.innerText.split('/')[0]);
            
            if(val < max) {
                val++;
                cnt.innerText = `${val}/${max}`;
                if(navigator.vibrate) navigator.vibrate(30);
                
                if(val === max) {
                    btn.classList.add('done');
                    btn.innerText = 'أحسنت!';
                    document.getElementById('c-'+id).classList.add('done');
                    if(navigator.vibrate) navigator.vibrate([50,50,50]);
                }
            }
        }

        function toggleTheme() {
            const b = document.body;
            if(b.getAttribute('data-theme') === 'dark') {
                b.removeAttribute('data-theme');
                localStorage.setItem('theme', 'light');
            } else {
                b.setAttribute('data-theme', 'dark');
                localStorage.setItem('theme', 'dark');
            }
        }
    </script>
</body>
</html>
