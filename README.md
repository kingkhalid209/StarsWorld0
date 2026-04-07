<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="mobile-web-app-capable" content="yes">
    <title>حاسبة الميزانية الذكية - StarsWorld0</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;900&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary: #111827; /* أسود فخم */
            --accent: #3b82f6; /* أزرق ثقة */
            --success: #10b981; /* أخضر تشجيعي */
            --bg-gradient: linear-gradient(135deg, #f3f4f6 0%, #e5e7eb 100%);
            --card-bg: rgba(255, 255, 255, 0.95);
            --text-main: #1f2937;
            --text-muted: #6b7280;
        }

        body { 
            font-family: 'Tajawal', sans-serif; 
            background: var(--bg-gradient); 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            min-height: 100vh; 
            margin: 0; 
            padding: 20px; 
        }

        .card { 
            background: var(--card-bg); 
            backdrop-filter: blur(10px);
            padding: 40px 25px; 
            border-radius: 28px; 
            box-shadow: 0 25px 50px -12px rgba(0,0,0,0.15); 
            width: 100%; 
            max-width: 420px; 
            text-align: center; 
            border: 1px solid rgba(255,255,255,0.6);
            position: relative;
            overflow: hidden;
        }

        /* شريط تسويقي علوي */
        .promo-bar {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            background: linear-gradient(90deg, #10b981, #059669);
            color: white;
            font-size: 0.8rem;
            font-weight: 700;
            padding: 6px 0;
            letter-spacing: 0.5px;
        }

        .brand { 
            background: var(--primary); 
            color: #fff; 
            padding: 8px 25px; 
            border-radius: 50px; 
            display: inline-block; 
            font-size: 0.95rem; 
            font-weight: 900; 
            margin-top: 15px;
            margin-bottom: 10px; 
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        h2 { 
            color: var(--text-main); 
            margin-bottom: 5px; 
            font-size: 1.6rem; 
            font-weight: 900; 
        }

        .subtitle {
            color: var(--text-muted);
            font-size: 0.9rem;
            font-weight: 500;
            margin-bottom: 25px;
        }

        .input-group { 
            text-align: right; 
            margin-bottom: 20px; 
            position: relative;
        }

        label { 
            display: block; 
            margin-bottom: 8px; 
            font-weight: 700; 
            color: var(--text-main); 
            font-size: 0.95rem; 
        }

        input, select { 
            width: 100%; 
            padding: 16px 16px 16px 40px; 
            border: 2px solid #e5e7eb; 
            border-radius: 16px; 
            box-sizing: border-box; 
            font-size: 1.05rem; 
            font-family: 'Tajawal', sans-serif;
            font-weight: 700;
            color: var(--text-main);
            background: #f9fafb; 
            transition: all 0.3s ease; 
            outline: none; 
            appearance: none; 
        }

        input:focus, select:focus { 
            border-color: var(--primary); 
            background: #fff; 
            box-shadow: 0 0 0 4px rgba(17, 24, 39, 0.05);
        }

        @keyframes fadeInScale {
            0% { opacity: 0; transform: scale(0.95) translateY(10px); }
            100% { opacity: 1; transform: scale(1) translateY(0); }
        }

        .results { 
            margin-top: 25px; 
            display: none; 
            animation: fadeInScale 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        .result-card { 
            padding: 20px; 
            border-radius: 20px; 
            text-align: center; 
            border: 2px solid #34d399; 
            background: linear-gradient(to bottom, #ffffff, #ecfdf5);
            position: relative;
        }

        .marketing-badge {
            position: absolute;
            top: -12px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--primary);
            color: white;
            padding: 4px 15px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 700;
            white-space: nowrap;
        }

        .installment-box {
            margin-bottom: 15px;
        }

        .val-title { font-size: 0.9rem; color: var(--text-muted); font-weight: 700; }
        .val-amount { font-size: 2.2rem; color: var(--primary); font-weight: 900; line-height: 1.2; }
        .val-currency { font-size: 1rem; color: var(--text-muted); font-weight: 700; }

        .divider { height: 1px; background: #a7f3d0; margin: 15px 0; }

        .remain-box {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: white;
            padding: 12px 15px;
            border-radius: 14px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.02);
        }

        .remain-text { font-size: 0.85rem; font-weight: 700; color: var(--text-main); }
        .remain-val { font-size: 1.2rem; font-weight: 900; color: var(--success); }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(17, 24, 39, 0.4); }
            70% { box-shadow: 0 0 0 15px rgba(17, 24, 39, 0); }
            100% { box-shadow: 0 0 0 0 rgba(17, 24, 39, 0); }
        }

        .shop-btn { 
            display: flex; 
            justify-content: center;
            align-items: center;
            gap: 8px;
            width: 100%; 
            padding: 18px; 
            margin-top: 25px; 
            background: linear-gradient(90deg, #111827, #374151);
            color: #fff !important; 
            text-decoration: none !important; 
            border-radius: 16px; 
            font-weight: 900; 
            font-size: 1.15rem; 
            transition: all 0.3s ease; 
            cursor: pointer;
            box-shadow: 0 10px 20px rgba(17, 24, 39, 0.2);
            animation: pulse 2.5s infinite;
        }

        .tabby-promo {
            display: none;
            color: #059669;
            font-size: 0.85rem;
            font-weight: 700;
            margin-top: 10px;
        }

        /* تنسيق إخلاء المسؤولية */
        .disclaimer-box {
            margin-top: 20px;
            padding-top: 15px;
            border-top: 1px solid #e5e7eb;
            width: 100%;
        }

        .disclaimer-text {
            font-size: 0.72rem;
            color: #9ca3af;
            line-height: 1.4;
            text-align: center;
            margin: 0;
        }
    </style>
</head>
<body>

<div class="card">
    <div class="promo-bar">⚡ تسوق بذكاء و قسّط براحتك</div>
    
    <div class="brand">StarsWorld0</div>
    <h2>اكتشف قدرتك الشرائية</h2>
    <div class="subtitle">خطط لمشترياتك بدون أي ضغط مالي على ميزانيتك</div>
    
    <div class="input-group">
        <label>الراتب الشهري:</label>
        <input type="number" id="salary" placeholder="أدخل راتبك (ر.س)" oninput="calculate()">
    </div>

    <div class="input-group">
        <label>قيمة السلة أو المنتج:</label>
        <input type="number" id="price" placeholder="أدخل السعر (ر.س)" oninput="calculate()">
    </div>

    <div class="input-group">
        <label>خطة الدفع المفضلة:</label>
        <select id="months" onchange="calculate()">
            <option value="1">دفع فوري (كاش)</option>
            <option value="2">على دفعتين</option>
            <option value="3">3 دفعات</option>
            <option value="4" selected>4 دفعات (تابي / تمارا) 🔥</option>
            <option value="6">6 أشهر</option>
            <option value="12">12 شهر (سنة)</option>
            <option value="24">24 شهر (سنتين)</option>
            <option value="36">36 شهر (3 سنوات)</option>
        </select>
    </div>

    <div id="resultArea" class="results">
        <div class="result-card">
            <div class="marketing-badge" id="badgeText">ميزانيتك تسمح ✅</div>
            <div class="installment-box">
                <div class="val-title" id="typeLabel">القسط الشهري المريح:</div>
                <div class="val-amount"><span id="monthlyVal">0</span> <span class="val-currency">ر.س</span></div>
            </div>
            <div id="tabbyPromo" class="tabby-promo">✨ متوافق مع تابي و تمارا (بدون فوائد)</div>
            <div class="divider"></div>
            <div class="remain-box">
                <span class="remain-text">يتبقى لروتينك اليومي:</span>
                <span class="remain-val"><span id="remainVal">0</span> ر.س</span>
            </div>
        </div>
        
        <a href="https://starsworld0.com" target="_top" class="shop-btn">أكمل طلبك الآن بثقة 🛒</a>

        <div class="disclaimer-box">
            <p class="disclaimer-text">
                <b>إخلاء مسؤولية:</b> الحسبة تقديرية؛ تتوفر خيارات تقسيط <b>(4 دفعات أو أكثر)</b> حسب سياسة مزودي الخدمة المتاحة لك عند إتمام الطلب.
            </p>
        </div>
    </div>
</div>

<script>
    function calculate() {
        const salary = parseFloat(document.getElementById('salary').value);
        const price = parseFloat(document.getElementById('price').value);
        const months = parseInt(document.getElementById('months').value);
        const resultArea = document.getElementById('resultArea');
        const tabbyPromo = document.getElementById('tabbyPromo');
        const badgeText = document.getElementById('badgeText');

        if (salary > 0 && price > 0) {
            resultArea.style.display = 'block';
            const installment = price / months;
            const remaining = salary - installment;

            document.getElementById('monthlyVal').innerText = installment.toLocaleString(undefined, {minimumFractionDigits: 0, maximumFractionDigits: 0});
            document.getElementById('remainVal').innerText = remaining.toLocaleString(undefined, {minimumFractionDigits: 0, maximumFractionDigits: 0});

            if (months === 1) {
                document.getElementById('typeLabel').innerText = "قيمة الدفع الفوري:";
                tabbyPromo.style.display = 'none';
                badgeText.innerText = "دفع كاش سريع ⚡";
            } else if (months === 4) {
                document.getElementById('typeLabel').innerText = "القسط الشهري المريح:";
                tabbyPromo.style.display = 'block';
                badgeText.innerText = "الخيار الأكثر طلباً 🔥";
            } else {
                document.getElementById('typeLabel').innerText = "القسط الشهري المريح:";
                tabbyPromo.style.display = 'none';
                badgeText.innerText = "قسطها و ارتاح ✅";
            }
            
            if (remaining < 0) {
                badgeText.innerText = "القسط يتجاوز الراتب ⚠️";
                badgeText.style.backgroundColor = "#ef4444";
            } else {
                badgeText.style.backgroundColor = "var(--primary)";
            }
        } else {
            resultArea.style.display = 'none';
        }
    }
</script>
</body>
</html>


