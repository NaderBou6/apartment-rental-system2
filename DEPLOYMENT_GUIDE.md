# دليل النشر - رفع التطبيق على الإنترنت

## 🎯 الهدف
رفع نظام إدارة كراء الشقق اليومية على الإنترنت مجاناً مع قاعدة بيانات كاملة

## 📋 ما سنحتاجه
- حساب Supabase مجاني (قاعدة البيانات)
- حساب Vercel أو Netlify مجاني (الاستضافة)
- 15-20 دقيقة من وقتك

---

## 🗄️ الجزء الأول: إعداد قاعدة البيانات (Supabase)

### الخطوة 1: إنشاء حساب Supabase
1. اذهب إلى: https://supabase.com
2. اضغط "Start your project"
3. اختر "Sign up" 
4. سجل باستخدام GitHub أو Google (الأسهل)

### الخطوة 2: إنشاء مشروع جديد
1. بعد تسجيل الدخول، اضغط "New Project"
2. اختر Organization (أو أنشئ واحد جديد)
3. املأ البيانات:
   - **Project Name**: `apartment-rental-system`
   - **Database Password**: اختر كلمة مرور قوية واحفظها!
   - **Region**: اختر `West Europe (Ireland)` للسرعة
4. اضغط "Create new project"
5. انتظر 2-3 دقائق حتى يكتمل الإعداد

### الخطوة 3: إعداد قاعدة البيانات
1. في لوحة تحكم المشروع، اذهب إلى **SQL Editor**
2. اضغط "New query"
3. انسخ كامل محتوى ملف `database/schema.sql` من مشروعك
4. الصق في SQL Editor
5. اضغط "Run" أو اضغط Ctrl+Enter
6. يجب أن ترى رسالة "Success. No rows returned"

### الخطوة 4: الحصول على مفاتيح API
1. اذهب إلى **Settings** > **API**
2. انسخ هذه المعلومات (ستحتاجها لاحقاً):
   - **Project URL**: `https://xxxxx.supabase.co`
   - **anon public key**: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...`

### الخطوة 5: إعداد Authentication
1. اذهب إلى **Authentication** > **Settings**
2. في **Site URL** ضع مؤقتاً: `http://localhost:3000`
3. سنحدثه لاحقاً برابط الموقع النهائي

---

## 🌐 الجزء الثاني: رفع التطبيق (Vercel - الأسهل)

### الخطوة 1: تحضير الملفات
1. افتح ملف `js/config.js`
2. استبدل:
```javascript
export const supabaseConfig = {
    url: 'YOUR_SUPABASE_URL', // ضع Project URL هنا
    anonKey: 'YOUR_SUPABASE_ANON_KEY' // ضع anon public key هنا
};
```

بالمعلومات الحقيقية من Supabase:
```javascript
export const supabaseConfig = {
    url: 'https://your-project-id.supabase.co',
    anonKey: 'your-actual-anon-key-here'
};
```

### الخطوة 2: إنشاء حساب Vercel
1. اذهب إلى: https://vercel.com
2. اضغط "Sign Up"
3. اختر "Continue with GitHub" (الأسهل)
4. أكمل إنشاء الحساب

### الخطوة 3: رفع المشروع
#### الطريقة الأولى: Drag & Drop (الأسهل)
1. في لوحة تحكم Vercel، اضغط "Add New..." > "Project"
Quick setup — if you've done this kind of thing before

Get started by creating a new file or uploading an existing file.
We recommend every repository include a README, LICENSE, and .gitignore.

[Create new file] [Upload files] ← هذا الزر
2. اسحب مجلد المشروع كاملاً إلى منطقة الرفع
3. أو اضغط "Browse" واختر مجلد `ADP/APP`
4. اضغط "Deploy"
5. انتظر 2-3 دقائق

#### الطريقة الثانية: GitHub (للمتقدمين)
1. ارفع المشروع إلى GitHub أولاً
2. في Vercel، اضغط "Import Git Repository"
3. اختر المشروع من GitHub
4. اضغط "Deploy"

### الخطوة 4: الحصول على رابط الموقع
1. بعد اكتمال النشر، ستحصل على رابط مثل:
   `https://your-project-name.vercel.app`
2. انسخ هذا الرابط

### الخطوة 5: تحديث إعدادات Supabase
1. ارجع إلى لوحة تحكم Supabase
2. اذهب إلى **Authentication** > **Settings**
3. في **Site URL** ضع رابط موقعك الجديد:
   `https://your-project-name.vercel.app`
4. اضغط "Save"

---

## 🌐 البديل: Netlify (سهل أيضاً)

### إذا فضلت Netlify بدلاً من Vercel:

1. **إنشاء حساب**: اذهب إلى https://netlify.com
2. **رفع المشروع**: اسحب مجلد المشروع إلى Netlify
3. **الحصول على الرابط**: انسخ رابط الموقع
4. **تحديث Supabase**: ضع الرابط الجديد في Site URL

---

## ✅ اختبار التطبيق

### بعد اكتمال النشر:
1. افتح رابط موقعك الجديد
2. جرب إنشاء حساب جديد
3. سجل دخول
4. أضف شقة تجريبية
5. أضف حجز تجريبي
6. تحقق من الإحصائيات

---

## 🔧 استكشاف الأخطاء

### إذا لم يعمل التطبيق:

#### خطأ في الاتصال بقاعدة البيانات:
- تحقق من مفاتيح Supabase في `config.js`
- تأكد من تشغيل SQL schema بنجاح
- تحقق من Site URL في إعدادات Supabase

#### خطأ في تحميل الملفات:
- تأكد من رفع جميع الملفات
- تحقق من مسارات الملفات في HTML

#### خطأ في التسجيل:
- تحقق من إعدادات Authentication في Supabase
- تأكد من Site URL الصحيح

---

## 🎉 تهانينا!

إذا اتبعت هذه الخطوات، ستحصل على:
- ✅ موقع ويب يعمل على الإنترنت
- ✅ قاعدة بيانات مجانية وآمنة
- ✅ نظام تسجيل دخول كامل
- ✅ جميع ميزات التطبيق تعمل

---

## 📞 الدعم

إذا واجهت أي مشكلة:
1. تحقق من هذا الدليل مرة أخرى
2. راجع رسائل الخطأ في Developer Tools (F12)
3. تأكد من جميع الإعدادات في Supabase و Vercel

**الموقع سيكون متاح 24/7 مجاناً!** 🚀