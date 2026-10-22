<!DOCTYPE html>
<html lang="ar" dir="rtl" translate="no" class="notranslate">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>OSCAR XV - Security Check</title>
<style>
  :root {
    --bg: #090510;
    --card-bg: #150f21;
    --text-main: #ffffff;
    --text-muted: #9a8fae;
    
    /* اللون البنفسجي */
    --purple: #8b5cf6; 
    --purple-glow: rgba(139, 92, 246, 0.5);
    --purple-dark: #7c3aed;
    
    /* لون التحقق (أخضر باش يبان مقبول) */
    --green: #22c55e;
    --green-bg: rgba(34, 197, 94, 0.1);
    
    --font-main: 'Segoe UI', system-ui, -apple-system, sans-serif;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background-color: var(--bg);
    color: var(--text-main);
    font-family: var(--font-main);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-image: 
      linear-gradient(rgba(139, 92, 246, 0.05) 1px, transparent 1px),
      linear-gradient(90deg, rgba(139, 92, 246, 0.05) 1px, transparent 1px);
    background-size: 40px 40px;
    overflow: hidden;
    padding: 20px;
  }

  /* الحاوية الرئيسية (البطاقة) */
  .main-card {
    width: 100%;
    max-width: 420px;
    background: var(--card-bg);
    border-radius: 24px;
    padding: 40px 30px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.6), inset 0 0 0 1px rgba(139, 92, 246, 0.15);
    position: relative;
    text-align: center;
    animation: fadeIn 0.6s ease-out;
  }

  /* شريط الإضاءة البنفسجي فوق */
  .main-card::before {
    content: '';
    position: absolute;
    top: 0; left: 10%; right: 10%; height: 2px;
    background: linear-gradient(90deg, transparent, var(--purple), transparent);
    border-radius: 50%;
    box-shadow: 0 0 15px var(--purple);
  }

  @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

  /* الشعار */
  .logo {
    font-size: 38px;
    font-weight: 900;
    font-style: italic;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 20px;
    text-shadow: 0 0 20px rgba(139, 92, 246, 0.3);
    direction: ltr; /* باش يبان مزيان */
  }

  .logo span { color: var(--purple); }

  /* الخط البنفسجي تحت الشعار */
  .line {
    width: 60px;
    height: 3px;
    background-color: var(--purple);
    margin: 0 auto 20px;
    border-radius: 3px;
    box-shadow: 0 0 12px var(--purple);
  }

  /* النصوص الفرعية */
  .subtitle {
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 3px;
    color: var(--text-muted);
    text-transform: uppercase;
    margin-bottom: 35px;
    direction: ltr;
  }

  /* صندوق التحقق الأخضر */
  .verify-box {
    border: 1px solid var(--green);
    background: var(--green-bg);
    border-radius: 12px;
    padding: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    color: var(--green);
    font-weight: 600;
    font-size: 15px;
    margin-bottom: 30px;
    box-shadow: 0 0 20px rgba(34, 197, 94, 0.1);
    transition: all 0.3s ease;
  }

  /* شبيه كلاودفلير */
  .cf-widget {
    background: #1e1629;
    border-radius: 12px;
    padding: 15px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 25px;
    border: 1px solid rgba(139, 92, 246, 0.2);
  }
  .cf-left { text-align: left; direction: ltr; font-family: monospace; font-size: 12px; font-weight: bold; color: #fff; }
  .cf-right { display: flex; align-items: center; gap: 12px; color: #fff; font-size: 14px; font-weight: 600; }
  .cf-icon {
    width: 32px; height: 32px; background: #4b3c61; border-radius: 50%;
    display: flex; align-items: center; justify-content: center; font-size: 18px; transition: 0.3s;
  }

  /* الفوتر النصي */
  .footer-text {
    font-size: 13px;
    color: var(--text-muted);
    line-height: 1.8;
  }
  .footer-text span { color: var(--green); }

  /* ---------------- الصفحة الثانية (التوليد) ---------------- */
  .page-2 { display: none; }
  .page-2 .subtitle { margin-bottom: 25px; }

  /* اختيار المدة */
  .duration-select {
    width: 100%;
    background: rgba(0,0,0,0.3);
    border: 1px solid rgba(139, 92, 246, 0.3);
    color: #fff;
    padding: 15px;
    border-radius: 12px;
    font-size: 15px;
    font-family: inherit;
    margin-bottom: 20px;
    outline: none;
    cursor: pointer;
    appearance: none;
    text-align: center;
  }
  .duration-select:focus { border-color: var(--purple); }
  .duration-select option { background: var(--card-bg); color: #fff; }

  /* الزر البنفسجي الكبير */
  .btn-primary {
    width: 100%;
    background: var(--purple);
    color: white;
    border: none;
    padding: 18px;
    border-radius: 12px;
    font-size: 16px;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 1px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    box-shadow: 0 0 25px var(--purple-glow);
    transition: all 0.3s ease;
  }
  .btn-primary:hover {
    background: var(--purple-dark);
    box-shadow: 0 0 35px rgba(139, 92, 246, 0.7);
  }

  /* عرض المفتاح بعد التوليد */
  .key-result {
    display: none;
    background: rgba(0,0,0,0.4);
    border: 1px dashed var(--purple);
    border-radius: 12px;
    padding: 20px;
    margin-top: 20px;
    animation: slideUp 0.4s ease;
  }
  .key-result.active { display: block; }
  .key-title { font-size: 12px; color: var(--purple); margin-bottom: 10px; letter-spacing: 1px; font-weight: bold; }
  .key-text {
    font-family: monospace;
    font-size: 18px;
    color: #fff;
    font-weight: bold;
    word-break: break-all;
    direction: ltr;
    margin-bottom: 15px;
    letter-spacing: 1px;
  }
  .btn-copy {
    background: rgba(139, 92, 246, 0.2);
    color: #fff;
    border: none;
    padding: 10px 20px;
    border-radius: 8px;
    cursor: pointer;
    font-family: inherit;
    font-weight: bold;
    transition: 0.2s;
    width: 100%;
  }
  .btn-copy:hover { background: rgba(139, 92, 246, 0.4); }

  @keyframes slideUp { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

</style>
</head>
<body>

  <!-- ================= الصفحة 1: التحقق ================= -->
  <div class="main-card page-1" id="page1">
    <div class="logo">OSCAR <span>XV</span></div>
    <div class="line"></div>
    <div class="subtitle">SECURITY CHECK</div>

    <div class="verify-box" id="verifyMsg">
      <span>⏳</span> جارٍ التحقق من المتصفح...
    </div>

    <div class="cf-widget">
      <div class="cf-left">
        CLOUDFLARE<br>
        <span style="font-size:9px; color:#9a8fae; font-weight:normal;">Privacy • Help</span>
      </div>
      <div class="cf-right">
        <span id="cfText">جارٍ التحقق...</span>
        <div class="cf-icon" id="cfIcon">✓</div>
      </div>
    </div>

    <div class="footer-text">
      <div><span>☑</span> سيتم تحويلك تلقائياً بعد التحقق</div>
      <div style="margin-top:5px;">🔒 خطوة واحدة لحماية موقعنا</div>
    </div>
  </div>

  <!-- ================= الصفحة 2: توليد المفتاح ================= -->
  <div class="main-card page-2" id="page2">
    <div class="logo">OSCAR <span>XV</span></div>
    <div class="line"></div>
    <div class="subtitle">SECURITY ACCESS</div>

    <div class="verify-box" style="margin-bottom: 20px;">
      <span>☑</span> تم التحقق بنجاح — انقر على الزر
    </div>

    <!-- اختيار المدة -->
    <select class="duration-select" id="duration">
      <option value="1">يوم واحد (24 ساعة)</option>
      <option value="7" selected>7 أيام</option>
      <option value="30">30 يوم</option>
      <option value="permanent">دائم (Permanent)</option>
    </select>

    <!-- زر الحصول على المفتاح -->
    <button class="btn-primary" id="getKeyBtn">
      <span style="font-size: 20px;">⌖</span> احصل على مفتاحك
    </button>

    <!-- عرض المفتاح -->
    <div class="key-result" id="keyResult">
      <div class="key-title">✓ مفتاح الترخيص الخاص بك</div>
      <div class="key-text" id="keyText">---</div>
      <button class="btn-copy" id="copyBtn">نسخ المفتاح</button>
    </div>
  </div>

<script>
  // -------- 1. منطق صفحة التحقق --------
  setTimeout(() => {
    // تغيير نص التحقق إلى أخضر
    const vMsg = document.getElementById('verifyMsg');
    vMsg.innerHTML = '<span>✅</span> تم التحقق! جارٍ التحويل...';
    
    // تغيير ويدجت كلاودفلير
    document.getElementById('cfText').textContent = 'تم بنجاح!';
    const cfIcon = document.getElementById('cfIcon');
    cfIcon.style.background = '#22c55e';
    cfIcon.textContent = '✓';

    // الانتقال للصفحة الثانية بعد ثانية ونصف
    setTimeout(() => {
      document.getElementById('page1').style.display = 'none';
      document.getElementById('page2').style.display = 'block';
    }, 1500);

  }, 2500); // وقت وهمي للتحقق

  // -------- 2. منطق توليد المفتاح --------
  const getKeyBtn = document.getElementById('getKeyBtn');
  const keyResult = document.getElementById('keyResult');
  const keyText = document.getElementById('keyText');
  const durationSelect = document.getElementById('duration');
  const copyBtn = document.getElementById('copyBtn');

  // دالة توليد مفتاح عشوائي
  function generateKey() {
    const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
    let key = 'OSXV-';
    for (let i = 0; i < 16; i++) {
      if (i > 0 && i % 4 === 0) key += '-';
      key += chars.charAt(Math.floor(Math.random() * chars.length));
    }
    return key;
  }

  // حدث الضغط على الزر
  getKeyBtn.addEventListener('click', () => {
    // تأثير وهمي للتحميل
    getKeyBtn.innerHTML = '<span>⏳</span> جارٍ التوليد...';
    getKeyBtn.disabled = true;
    getKeyBtn.style.opacity = '0.7';

    setTimeout(() => {
      const newKey = generateKey();
      const duration = durationSelect.value; // المدة المختارة
      
      // إظهار المفتاح
      keyText.textContent = newKey;
      keyResult.classList.add('active');
      
      // إعادة الزر لحالته
      getKeyBtn.innerHTML = '<span style="font-size: 20px;">⌖</span> احصل على مفتاحك';
      getKeyBtn.disabled = false;
      getKeyBtn.style.opacity = '1';
      
    }, 1000); // تأخير ثانية للشكل
  });

  // نسخ المفتاح
  copyBtn.addEventListener('click', () => {
    navigator.clipboard.writeText(keyText.textContent).then(() => {
      copyBtn.textContent = '✓ تم النسخ!';
      copyBtn.style.color = '#8b5cf6';
      setTimeout(() => {
        copyBtn.textContent = 'نسخ المفتاح';
        copyBtn.style.color = '#fff';
      }, 2000);
    }).catch(() => {
      alert('تعذر النسخ، يرجى النسخ يدوياً.');
    });
  });
</script>
</body>
</html>
