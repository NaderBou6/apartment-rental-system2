# ✅ قائمة التحقق قبل النشر

## 📋 تأكد من هذه النقاط قبل رفع التطبيق:

### 🗄️ قاعدة البيانات (Supabase)
- [ ] تم إنشاء حساب Supabase
- [ ] تم إنشاء مشروع جديد
- [ ] تم تشغيل SQL schema بنجاح
- [ ] تم نسخ Project URL
- [ ] تم نسخ anon public key

### ⚙️ إعدادات التطبيق
- [ ] تم تحديث `js/config.js` بمفاتيح Supabase الحقيقية
- [ ] تم التأكد من صحة المفاتيح (لا تحتوي على YOUR_SUPABASE_URL)
- [ ] جميع الملفات موجودة في المجلد

### 📁 الملفات المطلوبة
- [ ] `index.html` - الصفحة الرئيسية
- [ ] `demo.html` - النسخة التجريبية
- [ ] `css/style.css` - ملف الأنماط
- [ ] `js/main.js` - الكود الرئيسي
- [ ] `js/config.js` - الإعدادات (محدث)
- [ ] `js/supabase.js` - وظائف قاعدة البيانات
- [ ] `js/utils.js` - الوظائف المساعدة
- [ ] `database/schema.sql` - هيكل قاعدة البيانات
- [ ] `vercel.json` - إعدادات Vercel

### 🌐 الاستضافة
- [ ] تم إنشاء حساب Vercel أو Netlify
- [ ] جاهز لرفع المجلد كاملاً

---

## 🚀 خطوات النشر السريعة:

### 1️⃣ إعداد Supabase (5 دقائق)
```
1. supabase.com → Sign up
2. New Project → apartment-rental
3. SQL Editor → Run schema.sql
4. Settings → API → Copy URL & Key
```

### 2️⃣ تحديث الإعدادات (1 دقيقة)
```
1. افتح js/config.js
2. استبدل YOUR_SUPABASE_URL برابط مشروعك
3. استبدل YOUR_SUPABASE_ANON_KEY بالمفتاح
4. احفظ الملف
```

### 3️⃣ رفع التطبيق (3 دقائق)
```
1. vercel.com → Sign up with GitHub
2. Add New Project
3. اسحب مجلد ADP/APP
4. Deploy
```

### 4️⃣ تحديث Site URL (1 دقيقة)
```
1. ارجع إلى Supabase
2. Authentication → Settings
3. Site URL = رابط موقعك الجديد
4. Save
```

---

## 🔍 اختبار سريع:

بعد النشر، تأكد من:
- [ ] الموقع يفتح بدون أخطاء
- [ ] يمكن إنشاء حساب جديد
- [ ] يمكن تسجيل الدخول
- [ ] يمكن إضافة شقة
- [ ] يمكن إضافة حجز
- [ ] الإحصائيات تظهر

---

## 🆘 إذا لم يعمل شيء:

### خطأ في تحميل الصفحة:
- تحقق من رفع جميع الملفات
- تأكد من وجود index.html في المجلد الرئيسي

### خطأ في قاعدة البيانات:
- تحقق من مفاتيح config.js
- تأكد من تشغيل schema.sql في Supabase
- راجع Site URL في إعدادات Authentication

### خطأ في التسجيل:
- تحقق من Site URL في Supabase
- تأكد من تطابق رابط الموقع مع Site URL

---

## 📞 الدعم:

إذا واجهت أي مشكلة:
1. راجع هذه القائمة مرة أخرى
2. تحقق من Developer Tools (F12) لرسائل الخطأ
3. تأكد من جميع الخطوات في DEPLOY_NOW.md

**بالتوفيق! 🚀**