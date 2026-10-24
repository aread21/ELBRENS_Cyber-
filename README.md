<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ELBRENS_Cyber - الأمن السيبراني</title>
<style>
:root {
    --bg-dark: #07010e;
    --card-bg: rgba(24, 9, 40, 0.65);
    --card-border: rgba(255, 255, 255, 0.16);
    --text-main: #ffffff;
    --text-sub: #cbd5e1;
    --lec-color: #00e5ff;
    --sec-color: #00ff88;
    --gold-badge: #ffbe0b;
    --whatsapp-green: #25d366;
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--bg-dark);
    color: var(--text-main);
    min-height: 100vh;
    padding: 25px 15px;
    overflow-x: hidden;
    position: relative;
}

/* خلفية الجلو المتحركة */
.glow-canvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    z-index: -1;
    overflow: hidden;
    background: radial-gradient(circle at center, #18052b 0%, #05010a 100%);
}

.orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.8;
    mix-blend-mode: screen;
    animation: floatOrb 14s infinite alternate ease-in-out;
}

.orb-1 {
    width: 500px;
    height: 500px;
    background: radial-gradient(circle, #9d4edd, #5a189a);
    top: -10%;
    right: -10%;
}

.orb-2 {
    width: 460px;
    height: 460px;
    background: radial-gradient(circle, #b5179e, #800020);
    bottom: -12%;
    left: -8%;
    animation-delay: -4s;
}

.orb-3 {
    width: 360px;
    height: 360px;
    background: radial-gradient(circle, #ff007f, #7209b7);
    top: 35%;
    left: 35%;
    animation-delay: -8s;
}

.orb-4 {
    width: 300px;
    height: 300px;
    background: radial-gradient(circle, #9b002c, #3c096c);
    top: 15%;
    left: 10%;
    animation-delay: -2s;
}

@keyframes floatOrb {
    0% { transform: translate(0, 0) scale(1); }
    50% { transform: translate(60px, -40px) scale(1.12); }
    100% { transform: translate(-50px, 50px) scale(0.92); }
}

.container {
    max-width: 920px;
    margin: 0 auto;
    position: relative;
    z-index: 2;
}

header {
    text-align: center;
    margin-bottom: 24px;
}

header h1 {
    font-size: 2.5rem;
    font-weight: 900;
    background: linear-gradient(90deg, #ffffff, #e0aaff, #ff4d6d);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-shadow: 0 0 30px rgba(157, 78, 221, 0.5);
    margin-bottom: 8px;
    letter-spacing: 1px;
}

header p {
    color: var(--text-sub);
    font-size: 1rem;
}

/* شريط الحالة الذكي */
.smart-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 14px;
    padding: 0 6px;
    font-size: 0.88rem;
}

.today-indicator {
    background: rgba(157, 78, 221, 0.2);
    border: 1px solid rgba(199, 125, 255, 0.4);
    color: #e0aaff;
    padding: 5px 12px;
    border-radius: 20px;
    font-weight: 700;
    display: inline-flex;
    align-items: center;
    gap: 6px;
}

.save-toast {
    color: var(--sec-color);
    font-weight: 700;
    opacity: 0;
    transition: opacity 0.3s ease;
    display: inline-flex;
    align-items: center;
    gap: 5px;
}

.save-toast.show {
    opacity: 1;
}

/* شريط الفلترة والأزرار */
.controls-bar {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
    gap: 15px;
    align-items: end;
    background: rgba(255, 255, 255, 0.06);
    padding: 20px;
    border-radius: 20px;
    border: 1px solid var(--card-border);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    box-shadow: 0 10px 35px rgba(0, 0, 0, 0.45);
    margin-bottom: 20px;
}

/* شريط البحث */
.search-group {
    grid-column: 1 / -1;
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.search-group label {
    font-size: 0.95rem;
    color: #00e5ff;
    font-weight: 700;
}

.search-wrapper {
    position: relative;
    display: flex;
    align-items: center;
}

.search-input {
    width: 100%;
    padding: 14px 16px 14px 45px;
    border-radius: 12px;
    border: 1px solid rgba(0, 229, 255, 0.4);
    background: rgba(12, 3, 24, 0.9);
    color: #fff;
    font-size: 1rem;
    font-weight: 600;
    outline: none;
    transition: all 0.25s ease;
}

.search-input::placeholder {
    color: #94a3b8;
    font-weight: 400;
}

.search-input:focus {
    border-color: #ff4d6d;
    box-shadow: 0 0 18px rgba(255, 77, 109, 0.45);
}

.clear-search-btn {
    position: absolute;
    left: 12px;
    background: #ff4d6d;
    border: none;
    color: #fff;
    border-radius: 8px;
    width: 28px;
    height: 28px;
    display: none;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    font-size: 0.9rem;
    font-weight: bold;
}

.search-status {
    background: rgba(0, 229, 255, 0.12);
    border: 1px solid rgba(0, 229, 255, 0.35);
    color: #00e5ff;
    padding: 10px 16px;
    border-radius: 12px;
    margin-bottom: 18px;
    font-size: 0.95rem;
    font-weight: 700;
    display: none;
    align-items: center;
    justify-content: space-between;
}

.control-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.control-group label {
    font-size: 0.9rem;
    color: #e0aaff;
    font-weight: 700;
}

select {
    padding: 12px 14px;
    border-radius: 12px;
    border: 1px solid rgba(255, 255, 255, 0.25);
    background: rgba(12, 3, 24, 0.85);
    color: #fff;
    font-size: 1rem;
    font-weight: 600;
    outline: none;
    cursor: pointer;
    transition: all 0.25s ease;
}

select:hover, select:focus {
    border-color: #ff4d6d;
    box-shadow: 0 0 15px rgba(255, 77, 109, 0.4);
}

select option {
    background-color: #160428;
    color: #fff;
}

.action-buttons {
    grid-column: 1 / -1;
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
}

.show-btn {
    flex: 1;
    padding: 13px 22px;
    border-radius: 12px;
    border: none;
    background: linear-gradient(135deg, #9d4edd, #b5179e, #800020);
    color: #fff;
    font-size: 1.05rem;
    font-weight: 800;
    cursor: pointer;
    box-shadow: 0 0 20px rgba(181, 23, 158, 0.6);
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
}

.show-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 0 30px rgba(255, 0, 127, 0.85);
}

/* زر واتساب */
.whatsapp-btn {
    padding: 13px 20px;
    border-radius: 12px;
    border: 1px solid rgba(37, 211, 102, 0.5);
    background: rgba(37, 211, 102, 0.15);
    color: #25d366;
    font-size: 1.05rem;
    font-weight: 800;
    cursor: pointer;
    box-shadow: 0 0 15px rgba(37, 211, 102, 0.3);
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    text-decoration: none;
}

.whatsapp-btn:hover {
    background: var(--whatsapp-green);
    color: #fff;
    transform: translateY(-3px);
    box-shadow: 0 0 25px rgba(37, 211, 102, 0.7);
}

/* قائمة الكروت */
.schedule-list {
    display: flex;
    flex-direction: column;
    gap: 18px;
}

.card {
    background: var(--card-bg);
    backdrop-filter: blur(18px);
    -webkit-backdrop-filter: blur(18px);
    border: 1px solid var(--card-border);
    border-radius: 18px;
    padding: 22px 25px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
    position: relative;
    overflow: hidden;
    box-shadow: 0 8px 28px rgba(0, 0, 0, 0.4);
    transition: all 0.3s ease;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 14px 35px rgba(157, 78, 221, 0.35);
    border-color: rgba(255, 255, 255, 0.35);
}

.card::before {
    content: '';
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    width: 7px;
    background: var(--lec-color);
    box-shadow: 0 0 18px var(--lec-color);
}

.card.section::before {
    background: var(--sec-color);
    box-shadow: 0 0 18px var(--sec-color);
}

.card-info {
    flex: 1;
}

.title-row {
    display: flex;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
    margin-bottom: 12px;
}

.title-row h3 {
    font-size: 1.35rem;
    color: #fff;
}

.type-pill {
    font-size: 0.82rem;
    padding: 4px 12px;
    border-radius: 20px;
    font-weight: 700;
    background: rgba(0, 229, 255, 0.15);
    color: var(--lec-color);
    border: 1px solid rgba(0, 229, 255, 0.4);
}

.card.section .type-pill {
    background: rgba(0, 255, 136, 0.15);
    color: var(--sec-color);
    border: 1px solid rgba(0, 255, 136, 0.4);
}

.day-pill {
    font-size: 0.82rem;
    padding: 4px 12px;
    border-radius: 20px;
    font-weight: 700;
    background: rgba(255, 77, 109, 0.2);
    color: #ff8fa3;
    border: 1px solid rgba(255, 77, 109, 0.45);
}

.meta-item {
    margin: 7px 0;
    color: var(--text-sub);
    font-size: 1rem;
}

.meta-item strong {
    color: #fff;
}

.actions-row {
    display: flex;
    gap: 12px;
    margin-top: 16px;
    flex-wrap: wrap;
}

.btn-link {
    text-decoration: none;
    color: #fff;
    font-size: 0.9rem;
    font-weight: 700;
    padding: 9px 16px;
    border-radius: 10px;
    transition: all 0.25s ease;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    cursor: pointer;
}

.btn-link.platform {
    background: linear-gradient(135deg, rgba(157, 78, 221, 0.35), rgba(128, 0, 32, 0.45));
    border: 1px solid rgba(199, 125, 255, 0.45);
}

.btn-link.platform:hover {
    background: linear-gradient(135deg, #9d4edd, #800020);
    transform: translateY(-2px);
    box-shadow: 0 0 15px rgba(157, 78, 221, 0.7);
}

.btn-link.calendar {
    background: rgba(0, 229, 255, 0.15);
    border: 1px solid rgba(0, 229, 255, 0.4);
}

.btn-link.calendar:hover {
    background: rgba(0, 229, 255, 0.35);
    transform: translateY(-2px);
    box-shadow: 0 0 15px rgba(0, 229, 255, 0.6);
}

.card-timing {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    min-width: 180px;
}

.period-tag {
    background: linear-gradient(135deg, rgba(157, 78, 221, 0.4), rgba(128, 0, 32, 0.5));
    border: 1px solid rgba(255, 255, 255, 0.25);
    padding: 6px 14px;
    border-radius: 10px;
    font-size: 0.92rem;
    font-weight: 800;
    width: 100%;
    text-align: center;
}

.time-box {
    background: rgba(0, 0, 0, 0.6);
    border: 1px solid rgba(255, 255, 255, 0.15);
    padding: 12px 15px;
    border-radius: 12px;
    text-align: center;
    width: 100%;
}

.time-text {
    font-weight: 800;
    font-size: 1.02rem;
    display: block;
    direction: ltr;
    color: #fff;
}

.week-tag {
    display: block;
    font-size: 0.84rem;
    color: var(--gold-badge);
    margin-top: 6px;
    font-weight: 700;
}

.sec-tag {
    display: block;
    font-size: 0.8rem;
    color: #e2e8f0;
    margin-top: 4px;
}

.empty-box {
    background: var(--card-bg);
    backdrop-filter: blur(16px);
    border: 1px solid var(--card-border);
    border-radius: 18px;
    padding: 45px 20px;
    text-align: center;
    font-size: 1.25rem;
    line-height: 1.8;
}

@media (max-width: 650px) {
    .card {
        flex-direction: column;
        align-items: stretch;
    }
    .card-timing {
        width: 100%;
    }
}
</style>
</head>
<body>

<div class="glow-canvas">
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>
    <div class="orb orb-3"></div>
    <div class="orb orb-4"></div>
</div>

<div class="container">
    <header>
        <h1>ELBRENS_Cyber 🛡️✨</h1>
        <p>الفرقة الثانية (الأمن السيبراني) - جدول المحاضرات والسكاشن التفاعلي</p>
    </header>

    <div class="smart-bar">
        <span id="todayIndicator" class="today-indicator">📍 اليوم الحالي: ...</span>
        <span id="saveToast" class="save-toast">✅ تم حفظ اختياراتك تلقائياً</span>
    </div>

    <div class="controls-bar">
        <div class="search-group">
            <label for="searchInput">🔎 بحث شامل في الجدول (باسم المادة، الدكتور، المعيد، أو القاعة):</label>
            <div class="search-wrapper">
                <input type="text" id="searchInput" class="search-input" placeholder="اكتب هنا للبحث الفوري... (مثال: C++, Omar, A304, AI, Ramadan)">
                <button type="button" id="clearSearchBtn" class="clear-search-btn" title="مسح البحث">✕</button>
            </div>
        </div>

        <div class="control-group">
            <label for="daySelect">📅 اختر اليوم:</label>
            <select id="daySelect">
                <option value="الجمعة">الجمعة (Friday)</option>
                <option value="السبت">السبت (Day OFF)</option>
                <option value="الأحد">الأحد (Sunday)</option>
                <option value="الإثنين">الإثنين (Monday)</option>
                <option value="الثلاثاء">الثلاثاء (Tuesday)</option>
                <option value="الأربعاء">الأربعاء (Wednesday)</option>
                <option value="الخميس">الخميس (Day OFF)</option>
                <option value="كل الأيام" style="color:#00e5ff; font-weight:bold;">كل الأسبوع (All Days)</option>
            </select>
        </div>

        <div class="control-group">
            <label for="sectionSelect">👥 اختر السكشن (يُحفظ تلقائياً):</label>
            <select id="sectionSelect">
                <option value="1">سكشن 1</option>
                <option value="2">سكشن 2</option>
                <option value="3">سكشن 3</option>
                <option value="4">سكشن 4</option>
                <option value="5">سكشن 5</option>
                <option value="6">سكشن 6</option>
                <option value="7">سكشن 7</option>
                <option value="8">سكشن 8</option>
                <option value="9">سكشن 9</option>
                <option value="10">سكشن 10</option>
                <option value="11">سكشن 11</option>
                <option value="12">سكشن 12</option>
                <option value="13">سكشن 13</option>
                <option value="14">سكشن 14</option>
                <option value="15">سكشن 15</option>
                <option value="0" style="color:#00ff88; font-weight:bold;">عرض كل السكاشن (1-15)</option>
            </select>
        </div>

        <div class="control-group">
            <label for="weekSelect">🔄 اختر الأسبوع (يُحفظ تلقائياً):</label>
            <select id="weekSelect">
                <option value="1">الأسبوع الأول (Week 1)</option>
                <option value="2">الأسبوع الثاني (Week 2)</option>
            </select>
        </div>

        <div class="action-buttons">
            <button type="button" id="showBtn" class="show-btn">
                🔍 عرض الجدول
            </button>
            <a href="#" id="whatsappShareBtn" class="whatsapp-btn" title="مشاركة جدول اليوم على واتساب">
                💬 مشاركة واتساب
            </a>
        </div>
    </div>

    <div id="searchStatus" class="search-status"></div>
    <div id="scheduleList" class="schedule-list"></div>
</div>

<script>
var periodTimes = {
    1: "09:00 - 10:00",
    2: "10:00 - 11:00",
    3: "11:00 - 12:00",
    4: "12:00 - 01:00",
    5: "01:00 - 02:00",
    6: "02:00 - 03:00",
    7: "03:00 - 04:00",
    8: "04:00 - 05:00",
    9: "05:00 - 06:00"
};

var fridayTimes = {
    1: "09:00 - 10:00",
    2: "10:00 - 11:00",
    3: "11:00 - 12:00",
    4: "02:00 - 03:00",
    5: "03:00 - 04:00",
    6: "04:00 - 05:00",
    7: "05:00 - 06:00"
};

var dayOrder = {
    'الجمعة': 1,
    'السبت': 2,
    'الأحد': 3,
    'الإثنين': 4,
    'الثلاثاء': 5,
    'الأربعاء': 6,
    'الخميس': 7
};

var jsDaysToArabic = ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس', 'الجمعة', 'السبت'];

// روابط المنصات التعليمية
var omniaClassroomLink = 'https://classroom.google.com/c/ODI2NTM3ODk0MjEx?cjc=b3kqakze';
var ahmedYehiaLink = 'https://tremendous-starfish-d49.notion.site/3f74401206e980a0afbdd2904aee2c58?v=4614401206e983a997f9085395a3afc0&pvs=74';

var scheduleData = [
    // ==================== يوم الجمعة (Friday) ====================
    { day: 'الجمعة', p: 1, type: 'lecture', title: 'Programming For Cyber-Security', instructor: 'Dr. Abeer Hassan', loc1: 'A-New', sections: [1,2,3,4,5], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 2, type: 'lecture', title: 'Programming For Cyber-Security', instructor: 'Dr. Abeer Hassan', loc1: 'A-New', sections: [6,7,8,9,10], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 3, type: 'lecture', title: 'Programming For Cyber-Security', instructor: 'Dr. Abeer Hassan', loc1: 'A-New', sections: [11,12,13,14,15], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 4, type: 'lecture', title: 'Internet Application Development', instructor: 'Dr. Finan Nagy', loc1: 'G205', sections: [1,2,3,4], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 5, type: 'lecture', title: 'Internet Application Development', instructor: 'Dr. Finan Nagy', loc1: 'G205', sections: [5,6,7,8], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 6, type: 'lecture', title: 'Internet Application Development', instructor: 'Dr. Finan Nagy', loc1: 'G205', sections: [9,10,11,12], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 7, type: 'lecture', title: 'Internet Application Development', instructor: 'Dr. Finan Nagy', loc1: 'G205', sections: [13,14,15], weeks: [1,2], link: '#' },
    // سكاشن الجمعة
    { day: 'الجمعة', p: 1, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'A02', sections: [8], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 1, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'D105', sections: [11], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 1, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'G204', sections: [14,15], weeks: [2], link: '#' },
    { day: 'الجمعة', p: 2, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'D105', sections: [2], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 2, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'A02', sections: [11], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 2, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'G204', sections: [12,13], weeks: [2], link: '#' },
    { day: 'الجمعة', p: 3, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'A305', sections: [2], weeks: [2], link: '#' },
    { day: 'الجمعة', p: 3, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'D105', loc2: 'A305', sections: [3], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 3, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'A305', sections: [4], weeks: [2], link: '#' },
    { day: 'الجمعة', p: 3, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'A02', sections: [9], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 4, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'D105', loc2: 'A304', sections: [5], weeks: [1,2], link: '#' },
    { day: 'الجمعة', p: 4, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'G204', sections: [8,9], weeks: [2], link: '#' },
    { day: 'الجمعة', p: 4, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'A304', sections: [11], weeks: [2], link: '#' },
    { day: 'الجمعة', p: 4, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'A02', sections: [14], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 5, type: 'section', title: 'Internet App Development', instructor: 'Eng. Nadia', loc1: 'D105', sections: [4], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 5, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'G204', sections: [10,11], weeks: [2], link: '#' },
    { day: 'الجمعة', p: 5, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'A02', sections: [12], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 6, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'A02', sections: [13], weeks: [1], link: '#' },
    { day: 'الجمعة', p: 7, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'A02', sections: [10], weeks: [1], link: '#' },

    // ==================== يوم الأحد (Sunday) ====================
    { day: 'الأحد', p: 1, type: 'lecture', title: 'Network Security Protocol', instructor: 'Dr. Alaa Al-Shenhaby', loc1: 'A304', sections: [1,2,3,4], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 2, type: 'lecture', title: 'Network Security Protocol', instructor: 'Dr. Alaa Al-Shenhaby', loc1: 'A304', sections: [5,6,7,8], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 3, type: 'lecture', title: 'Network Security Protocol', instructor: 'Dr. Alaa Al-Shenhaby', loc1: 'A304', sections: [9,10,11,12], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 4, type: 'lecture', title: 'Network Security Protocol', instructor: 'Dr. Alaa Al-Shenhaby', loc1: 'A304', sections: [13,14,15], weeks: [1,2], link: '#' },
    // سكاشن الأحد
    { day: 'الأحد', p: 1, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'A01', sections: [9], weeks: [1], link: '#' },
    { day: 'الأحد', p: 1, type: 'section', title: 'Secured Network', instructor: 'Eng. Reem', loc1: 'F201', loc2: 'CNC', sections: [10], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 1, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Karim Adel', loc1: 'D103', sections: [15], weeks: [1], link: '#' },
    { day: 'الأحد', p: 2, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omnia', loc1: 'A01', sections: [1], weeks: [2], link: omniaClassroomLink },
    { day: 'الأحد', p: 2, type: 'section', title: 'Secured Network', instructor: 'Eng. Reem', loc1: 'F201', loc2: 'CNC', sections: [11], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 2, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'A01', sections: [12], weeks: [1], link: '#' },
    { day: 'الأحد', p: 3, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omnia', loc1: 'A01', sections: [2], weeks: [2], link: omniaClassroomLink },
    { day: 'الأحد', p: 3, type: 'section', title: 'Secured Network', instructor: 'Eng. Reem', loc1: 'F201', loc2: 'CNC', sections: [7], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 3, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'A01', sections: [8], weeks: [1], link: '#' },
    { day: 'الأحد', p: 4, type: 'section', title: 'Secured Network', instructor: 'Eng. Reem', loc1: 'F201', loc2: 'C103', sections: [6], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 5, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'PLC', sections: [2], weeks: [1], link: '#' },
    { day: 'الأحد', p: 5, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omnia', loc1: 'A01', sections: [4], weeks: [2], link: omniaClassroomLink },
    { day: 'الأحد', p: 5, type: 'section', title: 'Secured Network', instructor: 'Eng. Reem', loc1: 'F201', loc2: 'CNC', sections: [9], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 5, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'A01', sections: [10], weeks: [1], link: '#' },
    { day: 'الأحد', p: 6, type: 'section', title: 'Secured Network', instructor: 'Eng. Ahmed Yehia', loc1: 'A01', sections: [2], weeks: [1], link: ahmedYehiaLink },
    { day: 'الأحد', p: 6, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omnia', loc1: 'A01', sections: [3], weeks: [2], link: omniaClassroomLink },
    { day: 'الأحد', p: 6, type: 'section', title: 'Secured Network', instructor: 'Eng. Reem', loc1: 'F201', loc2: 'CNC', sections: [8], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 7, type: 'section', title: 'Secured Network', instructor: 'Eng. Ahmed Yehia', loc1: 'D101', sections: [4], weeks: [1], link: ahmedYehiaLink },
    { day: 'الأحد', p: 7, type: 'section', title: 'Secured Network', instructor: 'Eng. Reem', loc1: 'F201', loc2: 'CNC', sections: [5], weeks: [1,2], link: '#' },
    { day: 'الأحد', p: 7, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'G201', sections: [8,9], weeks: [2], link: '#' },
    { day: 'الأحد', p: 7, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'A01', sections: [13], weeks: [1], link: '#' },
    { day: 'الأحد', p: 8, type: 'section', title: 'Secured Network', instructor: 'Eng. Ahmed Yehia', loc1: 'A01', sections: [1], weeks: [1], link: ahmedYehiaLink },
    { day: 'الأحد', p: 9, type: 'section', title: 'Secured Network', instructor: 'Eng. Ahmed Yehia', loc1: 'A01', sections: [3], weeks: [1], link: ahmedYehiaLink },
    { day: 'الأحد', p: 9, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'G201', sections: [6,7], weeks: [2], link: '#' },

    // ==================== يوم الإثنين (Monday) ====================
    { day: 'الإثنين', p: 1, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [7], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 1, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'A01', sections: [14], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 2, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [5], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 2, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [6], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 2, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'A01', sections: [15], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 3, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [5], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 3, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [6], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 3, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Walaa Gomaa', loc1: 'A02', sections: [7], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 4, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Walaa Gomaa', loc1: 'A02', sections: [6], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 4, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [7], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 4, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [8], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 4, type: 'section', title: 'Secured Network', instructor: 'Eng. Shahd', loc1: 'A01', sections: [12], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 5, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Walaa Gomaa', loc1: 'A202', sections: [6], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 5, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Walaa Gomaa', loc1: 'G202', sections: [7], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 5, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [8], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 5, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [9], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 5, type: 'section', title: 'Secured Network', instructor: 'Eng. Shahd', loc1: 'A01', sections: [13], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 6, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'A303', sections: [1], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 6, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'G203', sections: [2], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 6, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [10], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 6, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [11], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 6, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'G203', sections: [12,13], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 6, type: 'section', title: 'Secured Network', instructor: 'Eng. Shahd', loc1: 'A01', sections: [14], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 7, type: 'section', title: 'Secured Network', instructor: 'Eng. Ahmed Yehia', loc1: 'G202', sections: [1,2], weeks: [2], link: ahmedYehiaLink },
    { day: 'الإثنين', p: 7, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'F-Seminar', sections: [4], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 7, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'A202', sections: [5], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 7, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [9], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 7, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'G105', sections: [10], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 7, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [12], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 7, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'G203', sections: [14,15], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 8, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [10], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 8, type: 'section', title: 'Secured Network', instructor: 'Eng. Shahd', loc1: 'G201', sections: [12,13], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 8, type: 'section', title: 'Secured Network', instructor: 'Eng. Shahd', loc1: 'A01', sections: [15], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 9, type: 'section', title: 'Secured Network', instructor: 'Eng. Ahmed Yehia', loc1: 'G202', sections: [3,4], weeks: [2], link: ahmedYehiaLink },
    { day: 'الإثنين', p: 9, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [12], weeks: [2], link: '#' },
    { day: 'الإثنين', p: 9, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [13], weeks: [1], link: '#' },
    { day: 'الإثنين', p: 9, type: 'section', title: 'Secured Network', instructor: 'Eng. Shahd', loc1: 'G201', sections: [14,15], weeks: [1], link: '#' },

    // ==================== يوم الثلاثاء (Tuesday) ====================
    { day: 'الثلاثاء', p: 1, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'A02', sections: [1], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 1, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omnia', loc1: 'C107', sections: [2,3], weeks: [1], link: omniaClassroomLink },
    { day: 'الثلاثاء', p: 1, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'A02', sections: [5], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 1, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'A01', sections: [11], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 2, type: 'section', title: 'C++ (Programming For Cyber Security)', instructor: 'Eng. Walaa Gomaa', loc1: 'A01', sections: [2], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 2, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'D101', sections: [13], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 2, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [14], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 3, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Walaa Gomaa', loc1: 'A01', sections: [7], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 3, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'A01', sections: [14], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 3, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'CNC', sections: [15], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 4, type: 'section', title: 'C++ (Programming For Cyber Security)', instructor: 'Eng. Walaa Gomaa', loc1: 'A01', sections: [4], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 4, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mahmoud', loc1: 'A02', sections: [4], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 4, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omar', loc1: 'A01', sections: [15], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 5, type: 'section', title: 'C++ (Programming For Cyber Security)', instructor: 'Eng. Walaa Gomaa', loc1: 'A01', sections: [5], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 6, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Walaa Gomaa', loc1: 'A202', sections: [2,3], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 6, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Walaa Gomaa', loc1: 'A01', sections: [6], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 7, type: 'section', title: 'C++ (Programming For Cyber Security)', instructor: 'Eng. Walaa Gomaa', loc1: 'A02', sections: [3], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 7, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Walaa Gomaa', loc1: 'A202', sections: [4,5], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 8, type: 'section', title: 'Programming For Cyber Security', instructor: 'Eng. Walaa Gomaa', loc1: 'A202', sections: [6,7], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 8, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'D105', sections: [8], weeks: [1], link: '#' },
    { day: 'الثلاثاء', p: 9, type: 'section', title: 'Network Security Protocol', instructor: 'Eng. Omnia', loc1: 'G203', sections: [1,4], weeks: [1], link: omniaClassroomLink },
    { day: 'الثلاثاء', p: 9, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'G201', sections: [8], weeks: [2], link: '#' },
    { day: 'الثلاثاء', p: 9, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'D103', loc2: 'G201', sections: [9], weeks: [1,2], link: '#' },

    // ==================== يوم الأربعاء (Wednesday) ====================
    { day: 'الأربعاء', p: 3, type: 'lecture', title: 'Artificial Intelligence', instructor: 'Dr. Muhammed Ramadan', loc1: 'G204', sections: [5,6,7,8], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 4, type: 'lecture', title: 'Specialized English', instructor: 'Dr. Ahmed Hassan', loc1: 'A-New', sections: [1,2,3,4,5], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 4, type: 'lecture', title: 'Artificial Intelligence', instructor: 'Dr. Muhammed Ramadan', loc1: 'G204', sections: [9,10,11,12], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 5, type: 'lecture', title: 'Specialized English', instructor: 'Dr. Ahmed Hassan', loc1: 'A-New', sections: [6,7,8,9,10], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 5, type: 'lecture', title: 'Artificial Intelligence', instructor: 'Dr. Muhammed Ramadan', loc1: 'G204', sections: [13,14,15], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 6, type: 'lecture', title: 'Artificial Intelligence', instructor: 'Dr. Muhammed Ramadan', loc1: 'G204', sections: [1,2,3,4], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 6, type: 'lecture', title: 'Specialized English', instructor: 'Dr. Ahmed Hassan', loc1: 'A-New', sections: [11,12,13,14,15], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 7, type: 'lecture', title: 'Secure Network', instructor: 'Dr. Muhammed Ramadan', loc1: 'A-New', sections: [6,7,8,9,10], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 8, type: 'lecture', title: 'Secure Network', instructor: 'Dr. Muhammed Ramadan', loc1: 'A-New', sections: [1,2,3,4,5], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 9, type: 'lecture', title: 'Secure Network', instructor: 'Dr. Muhammed Ramadan', loc1: 'A-New', sections: [11,12,13,14,15], weeks: [1,2], link: '#' },
    // سكاشن الأربعاء
    { day: 'الأربعاء', p: 1, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Nadia', loc1: 'D104', sections: [3], weeks: [2], link: '#' },
    { day: 'الأربعاء', p: 1, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'A01', sections: [15], weeks: [2], link: '#' },
    { day: 'الأربعاء', p: 2, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Nadia', loc1: 'G202', sections: [3,13,14], weeks: [1], link: '#' },
    { day: 'الأربعاء', p: 2, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Nadia', loc1: 'A01', sections: [11], weeks: [2], link: '#' },
    { day: 'الأربعاء', p: 3, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Nadia', loc1: 'D102', sections: [14], weeks: [2], link: '#' },
    { day: 'الأربعاء', p: 4, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Nadia', loc1: 'A01', sections: [13], weeks: [2], link: '#' },
    { day: 'الأربعاء', p: 5, type: 'section', title: 'Internet App Development', instructor: 'Eng. Walaa Gomaa', loc1: 'D105', sections: [1], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 5, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Nadia', loc1: 'A01', sections: [12], weeks: [2], link: '#' },
    { day: 'الأربعاء', p: 6, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'D102', sections: [7], weeks: [1], link: '#' },
    { day: 'الأربعاء', p: 7, type: 'section', title: 'C++ (Programming For Cyber Security)', instructor: 'Eng. Walaa Gomaa', loc1: 'D105', sections: [1], weeks: [1,2], link: '#' },
    { day: 'الأربعاء', p: 7, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'A304', sections: [15], weeks: [1], link: '#' },
    { day: 'الأربعاء', p: 8, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'A02', sections: [6], weeks: [1], link: '#' },
    { day: 'الأربعاء', p: 8, type: 'section', title: 'Internet Applications Development', instructor: 'Eng. Habiba', loc1: 'G203', sections: [10], weeks: [2], link: '#' },
    { day: 'الأربعاء', p: 8, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Nadia', loc1: 'G202', sections: [11,12], weeks: [1], link: '#' },
    { day: 'الأربعاء', p: 9, type: 'section', title: 'Artificial Intelligence', instructor: 'Eng. Mario', loc1: 'A02', sections: [10], weeks: [1], link: '#' }
];

function makeCalendarUrl(title, instructor, location, periodStr, dayName) {
    var text = encodeURIComponent(title + " - " + dayName);
    var details = encodeURIComponent("Instructor: " + instructor + " | Time: " + periodStr);
    var loc = encodeURIComponent(location);
    return "https://calendar.google.com/calendar/render?action=TEMPLATE&text=" + text + "&details=" + details + "&location=" + loc;
}

var toastTimeout;
function showSaveNotification() {
    var toast = document.getElementById('saveToast');
    if (!toast) return;
    toast.classList.add('show');
    clearTimeout(toastTimeout);
    toastTimeout = setTimeout(function() {
        toast.classList.remove('show');
    }, 2000);
}

function saveUserPreferences() {
    try {
        var secVal = document.getElementById('sectionSelect').value;
        var weekVal = document.getElementById('weekSelect').value;
        localStorage.setItem('elbrens_saved_section', secVal);
        localStorage.setItem('elbrens_saved_week', weekVal);
        showSaveNotification();
    } catch (e) {}
}

function initDefaultsAndStorage() {
    var todayIndex = new Date().getDay();
    var todayArabicName = jsDaysToArabic[todayIndex];
    var daySelectEl = document.getElementById('daySelect');
    var todayIndicatorEl = document.getElementById('todayIndicator');

    if (daySelectEl && todayArabicName) {
        daySelectEl.value = todayArabicName;
    }
    if (todayIndicatorEl && todayArabicName) {
        todayIndicatorEl.textContent = '📍 تم تحديد يوم النهاردة تلقائياً: ' + todayArabicName;
    }

    try {
        var savedSec = localStorage.getItem('elbrens_saved_section');
        var savedWeek = localStorage.getItem('elbrens_saved_week');

        if (savedSec !== null && document.getElementById('sectionSelect')) {
            document.getElementById('sectionSelect').value = savedSec;
        }
        if (savedWeek !== null && document.getElementById('weekSelect')) {
            document.getElementById('weekSelect').value = savedWeek;
        }
    } catch (e) {}
}

function updateWhatsAppShareLink(matches, day, sec, week) {
    var waBtn = document.getElementById('whatsappShareBtn');
    if (!waBtn) return;

    if (matches.length === 0 || day === 'السبت' || day === 'الخميس') {
        waBtn.setAttribute('href', 'https://wa.me/?text=' + encodeURIComponent('🛡️ ELBRENS_Cyber - الأمن السيبراني\nلا توجد محاضرات أو سكاشن مسجلة في يوم ' + day + '.'));
        return;
    }

    var secText = (sec === '0' || sec === 0) ? 'جميع السكاشن (1-15)' : 'سكشن ' + sec;
    var weekText = (week === '1' || week === 1) ? 'الأسبوع الأول' : 'الأسبوع الثاني';

    var msg = '🛡️ *جدول الفرقة الثانية (أمن سيبراني) - ELBRENS_Cyber*\n';
    msg += '📅 اليوم: *' + day + '* | 👥 ' + secText + ' | 🔄 ' + weekText + '\n';
    msg += '------------------------------------\n\n';

    for (var i = 0; i < matches.length; i++) {
        var m = matches[i];
        var isSec = (m.type === 'section');
        var typeLabel = isSec ? '📌 [سكشن]' : '📚 [محاضرة]';
        var loc = (week == 2 && m.loc2) ? m.loc2 : m.loc1;
        var tStr = (m.day === 'الجمعة') ? fridayTimes[m.p] : periodTimes[m.p];

        msg += typeLabel + ' *' + m.title + '*\n';
        msg += '🕒 الفترة P' + m.p + ' (' + tStr + ')\n';
        msg += '👤 الدكتور/المعيد: ' + m.instructor + '\n';
        msg += '📍 القاعة: ' + loc + '\n';
        if (m.link && m.link !== '#') {
            msg += '🌐 رابط المنصة: ' + m.link + '\n';
        }
        msg += '------------------------------------\n';
    }

    msg += '\n✨ _تم النشر عبر منصة ELBRENS_Cyber_';
    waBtn.setAttribute('href', 'https://api.whatsapp.com/send?text=' + encodeURIComponent(msg));
}

function renderSchedule() {
    var day = document.getElementById('daySelect').value;
    var sec = parseInt(document.getElementById('sectionSelect').value, 10);
    var week = parseInt(document.getElementById('weekSelect').value, 10);
    var searchInputEl = document.getElementById('searchInput');
    var rawQuery = searchInputEl ? searchInputEl.value.trim() : '';
    var searchQuery = rawQuery.toLowerCase();
    var clearBtn = document.getElementById('clearSearchBtn');
    var statusEl = document.getElementById('searchStatus');
    var listEl = document.getElementById('scheduleList');

    if (clearBtn) {
        clearBtn.style.display = searchQuery.length > 0 ? 'flex' : 'none';
    }

    listEl.innerHTML = '';

    if (searchQuery === '' && (day === 'السبت' || day === 'الخميس')) {
        statusEl.style.display = 'none';
        listEl.innerHTML = '<div class="empty-box">🎉 <strong>يوم إجازة رسمي (Day OFF)!</strong><br>لا توجد أي محاضرات أو سكاشن في يوم ' + day + '.</div>';
        updateWhatsAppShareLink([], day, sec, week);
        return;
    }

    var matches = [];
    for (var i = 0; i < scheduleData.length; i++) {
        var item = scheduleData[i];
        var loc1Str = item.loc1 || '';
        var loc2Str = item.loc2 || '';

        if (searchQuery !== '') {
            var inTitle = item.title.toLowerCase().indexOf(searchQuery) !== -1;
            var inInstructor = item.instructor.toLowerCase().indexOf(searchQuery) !== -1;
            var inLoc = loc1Str.toLowerCase().indexOf(searchQuery) !== -1 || loc2Str.toLowerCase().indexOf(searchQuery) !== -1;
            var inDay = item.day.toLowerCase().indexOf(searchQuery) !== -1;

            if (inTitle || inInstructor || inLoc || inDay) {
                matches.push(item);
            }
        } else {
            var sameDay = (day === 'كل الأيام') || (item.day === day);
            var sameWeek = (item.weeks.indexOf(week) !== -1);
            var sameSec = (sec === 0) || (item.sections.indexOf(sec) !== -1);

            if (sameDay && sameWeek && sameSec) {
                matches.push(item);
            }
        }
    }

    matches.sort(function(a, b) {
        if (a.day !== b.day) {
            return (dayOrder[a.day] || 99) - (dayOrder[b.day] || 99);
        }
        return a.p - b.p;
    });

    updateWhatsAppShareLink(matches, day, sec, week);

    if (searchQuery !== '') {
        statusEl.style.display = 'flex';
        statusEl.innerHTML = '<span>🔎 نتائج البحث الشامل في الجدول عن: <strong>"' + rawQuery + '"</strong></span>' +
                             '<span>تم العثور على (' + matches.length + ') نتيجة</span>';
    } else {
        statusEl.style.display = 'none';
    }

    if (matches.length === 0) {
        var emptyMsg = searchQuery !== ''
            ? '🔎 <strong>لا توجد أي مادة أو دكتور أو قاعة تطابق "' + rawQuery + '"</strong><br><span style="font-size:0.95rem; color:#cbd5e1;">جرب كتابة جزء من الاسم بالإنجليزية مثل: Network أو Omar أو A304 أو G204.</span>'
            : '✨ <strong>لا توجد محاضرات أو سكاشن مسجلة لـ (سكشن ' + sec + ') في يوم ' + day + ' (الأسبوع ' + week + ').</strong><br><span style="font-size:0.95rem; color:#cbd5e1;">جرب التبديل بين الأسبوع الأول والثاني أو اختر "عرض كل السكاشن".</span>';
        listEl.innerHTML = '<div class="empty-box">' + emptyMsg + '</div>';
        return;
    }

    var htmlContent = '';
    for (var j = 0; j < matches.length; j++) {
        var m = matches[j];
        var isSection = (m.type === 'section');
        var badgeText = isSection ? 'Section (سكشن عملي)' : 'Lecture (محاضرة)';
        var finalLocation = (week === 2 && m.loc2) ? m.loc2 : m.loc1;
        var timeStr = (m.day === 'الجمعة') ? fridayTimes[m.p] : periodTimes[m.p];

        var weekLabel = 'الأسبوع الأول والثاني (1, 2)';
        if (m.weeks.length === 1) {
            weekLabel = (m.weeks[0] === 1) ? 'الأسبوع الأول فقط (Week 1)' : 'الأسبوع الثاني فقط (Week 2)';
        } else if (m.loc2) {
            weekLabel = 'أسبوع 1: ' + m.loc1 + ' | أسبوع 2: ' + m.loc2;
        }

        var secRange = 'سكاشن: ' + m.sections.join(', ');
        var calUrl = makeCalendarUrl(m.title, m.instructor, finalLocation, timeStr, m.day);

        htmlContent += '<div class="card ' + (isSection ? 'section' : '') + '">' +
            '<div class="card-info">' +
                '<div class="title-row">' +
                    '<h3>' + m.title + '</h3>' +
                    '<span class="type-pill">' + badgeText + '</span>' +
                    '<span class="day-pill">📅 ' + m.day + '</span>' +
                '</div>' +
                '<p class="meta-item">👤 <strong>Instructor:</strong> ' + m.instructor + '</p>' +
                '<p class="meta-item">📍 <strong>Location:</strong> ' + finalLocation + '</p>' +
                '<div class="actions-row">' +
                    '<a href="' + m.link + '" target="_blank" class="btn-link platform">🌐 منصة المادة</a>' +
                    '<a href="' + calUrl + '" target="_blank" class="btn-link calendar">📅 تذكير بالموعد (تقويم جوجل)</a>' +
                '</div>' +
            '</div>' +
            '<div class="card-timing">' +
                '<div class="period-tag">🕒 الفترة (P' + m.p + ')</div>' +
                '<div class="time-box">' +
                    '<span class="time-text">⏰ ' + timeStr + '</span>' +
                    '<span class="week-tag">' + weekLabel + '</span>' +
                    '<span class="sec-tag">' + secRange + '</span>' +
                '</div>' +
            '</div>' +
        '</div>';
    }

    listEl.innerHTML = htmlContent;
}

// ربط الأحداث
document.getElementById('searchInput').addEventListener('input', renderSchedule);
document.getElementById('searchInput').addEventListener('keyup', renderSchedule);
document.getElementById('daySelect').addEventListener('change', renderSchedule);

document.getElementById('sectionSelect').addEventListener('change', function() {
    saveUserPreferences();
    renderSchedule();
});

document.getElementById('weekSelect').addEventListener('change', function() {
    saveUserPreferences();
    renderSchedule();
});

document.getElementById('showBtn').addEventListener('click', renderSchedule);

document.getElementById('clearSearchBtn').addEventListener('click', function() {
    var searchInput = document.getElementById('searchInput');
    searchInput.value = '';
    renderSchedule();
    searchInput.focus();
});

initDefaultsAndStorage();
renderSchedule();
</script>

</body>
</html>#
