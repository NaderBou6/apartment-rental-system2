# دليل الإعداد التفصيلي - نظام إدارة كراء الشقق اليومية

هذا الدليل يشرح خطوة بخطوة كيفية إعداد وتشغيل نظام إدارة كراء الشقق اليومية.

## المتطلبات الأساسية

### 1. Node.js
- تحميل وتثبيت Node.js من [nodejs.org](https://nodejs.org)
- الإصدار المطلوب: 16.0.0 أو أحدث
- للتحقق من التثبيت: `node --version`

### 2. محرر النصوص
- Visual Studio Code (مُوصى به)
- أو أي محرر نصوص آخر

### 3. متصفح ويب حديث
- Chrome, Firefox, Safari, Edge
- يجب دعم ES6 modules

## الخطوة 1: إعداد مشروع Supabase

### إنشاء حساب Supabase
1. اذهب إلى [supabase.com](https://supabase.com)
2. اضغط "Start your project"
3. سجل دخول باستخدام GitHub أو أنشئ حساب جديد

### إنشاء مشروع جديد
1. اضغط "New Project"
2. اختر Organization (أو أنشئ واحد جديد)
3. أدخل تفاصيل المشروع:
   - **Name**: apartment-rental-system
   - **Database Password**: كلمة مرور قوية (احفظها!)
   - **Region**: اختر الأقرب لموقعك
4. اضغط "Create new project"
5. انتظر 2-3 دقائق حتى يكتمل الإعداد

### الحصول على مفاتيح API
1. في لوحة تحكم المشروع، اذهب إلى **Settings** > **API**
2. انسخ المعلومات التالية:
   - **Project URL**: `https://xxxxx.supabase.co`
   - **anon public key**: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...`

## الخطوة 2: إعداد قاعدة البيانات

### تشغيل SQL Schema
1. في لوحة تحكم Supabase، اذهب إلى **SQL Editor**
2. اضغط "New query"
3. افتح ملف `database/schema.sql` من المشروع
4. انسخ كامل محتوى الملف
5. الصق في SQL Editor
6. اضغط "Run" أو Ctrl+Enter
7. تأكد من ظهور رسالة "Success" بدون أخطاء

### التحقق من إنشاء الجداول
1. اذهب إلى **Table Editor**
2. يجب أن ترى الجداول التالية:
   - `apartments`
   - `bookings`
   - `activities`
   - `user_profiles`

### إعداد Authentication
1. اذهب إلى **Authentication** > **Settings**
2. تأكد من تفعيل:
   - **Enable email confirmations**: حسب الحاجة
   - **Enable custom SMTP**: اختياري
3. في **URL Configuration**:
   - **Site URL**: `http://localhost:3000` (للتطوير)

## الخطوة 3: إعداد المشروع محلياً

### تحميل وتثبيت التبعيات
```bash
# الانتقال إلى مجلد المشروع
cd apartment-rental-manager

# تثبيت التبعيات
npm install
```

### تكوين ملف الإعدادات
1. افتح ملف `js/config.js`
2. استبدل القيم التالية بمعلومات مشروعك:

```javascript
export const supabaseConfig = {
    url: 'https://your-project-id.supabase.co', // ضع Project URL هنا
    anonKey: 'your-anon-key-here' // ضع anon public key هنا
};
```

### مثال على الإعدادات الصحيحة:
```javascript
export const supabaseConfig = {
    url: 'https://abcdefghijklmnop.supabase.co',
    anonKey: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImFiY2RlZmdoaWprbG1ub3AiLCJyb2xlIjoiYW5vbiIsImlhdCI6MTYzNjU0ODAwMCwiZXhwIjoxOTUyMTI0MDAwfQ.signature'
};
```

## الخطوة 4: تشغيل المشروع

### التشغيل في وضع التطوير
```bash
npm run dev
```

### النتيجة المتوقعة:
```
  VITE v4.4.5  ready in 500 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: use --host to expose
  ➜  press h to show help
```

### فتح المشروع
1. افتح المتصفح
2. اذهب إلى `http://localhost:3000`
3. يجب أن ترى صفحة تسجيل الدخول

## الخطوة 5: اختبار النظام

### إنشاء حساب جديد
1. اضغط "إنشاء حساب جديد"
2. أدخل البيانات:
   - **الاسم الكامل**: اسمك
   - **البريد الإلكتروني**: بريد صحيح
   - **كلمة المرور**: 8 أحرف على الأقل مع حرف كبير وصغير ورقم
3. اضغط "إنشاء الحساب"

### تسجيل الدخول
1. استخدم البريد وكلمة المرور
2. اضغط "تسجيل الدخول"
3. يجب أن تصل إلى لوحة التحكم

### إضافة شقة تجريبية
1. اذهب إلى قسم "الشقق"
2. اضغط "إضافة شقة جديدة"
3. أدخل البيانات:
   - **اسم الشقة**: شقة تجريبية
   - **الموقع**: الجزائر العاصمة
   - **السعر اليومي**: 5000
4. اضغط "حفظ"

### إضافة حجز تجريبي
1. اذهب إلى قسم "الحجوزات"
2. اضغط "إضافة حجز"
3. أدخل البيانات:
   - **الشقة**: اختر الشقة التي أضفتها
   - **تاريخ الدخول**: اليوم
   - **تاريخ الخروج**: غداً
   - **اسم النزيل**: اسم تجريبي
4. اضغط "حفظ الحجز"

## الخطوة 6: النشر على الإنترنت

### بناء المشروع للإنتاج
```bash
npm run build
```

### النشر على Vercel

#### الطريقة الأولى: Vercel CLI
```bash
# تثبيت Vercel CLI
npm install -g vercel

# تسجيل الدخول
vercel login

# نشر المشروع
vercel

# اتبع التعليمات:
# - اختر اسم المشروع
# - اختر الإعدادات الافتراضية
```

#### الطريقة الثانية: Vercel Dashboard
1. اذهب إلى [vercel.com](https://vercel.com)
2. سجل دخول باستخدام GitHub
3. اضغط "New Project"
4. اختر مجلد المشروع أو ارفعه
5. اضغط "Deploy"

### النشر على Netlify

#### الطريقة الأولى: Drag & Drop
1. شغل `npm run build`
2. اذهب إلى [netlify.com](https://netlify.com)
3. اسحب مجلد `dist` إلى منطقة الرفع
4. انتظر حتى يكتمل النشر

#### الطريقة الثانية: Git Integration
1. ارفع المشروع إلى GitHub
2. في Netlify، اضغط "New site from Git"
3. اختر GitHub repository
4. اضغط "Deploy site"

### تحديث إعدادات الإنتاج
بعد النشر، حدث إعدادات Supabase:
1. في لوحة تحكم Supabase، اذهب إلى **Authentication** > **Settings**
2. في **URL Configuration**:
   - **Site URL**: ضع رابط موقعك الجديد
   - مثال: `https://your-app.vercel.app`

## استكشاف الأخطاء الشائعة

### خطأ: "Invalid API key"
**السبب**: مفاتيح Supabase غير صحيحة
**الحل**:
1. تحقق من `js/config.js`
2. تأكد من نسخ المفاتيح بشكل صحيح
3. تأكد من عدم وجود مسافات إضافية

### خطأ: "Table doesn't exist"
**السبب**: لم يتم تشغيل SQL schema
**الحل**:
1. اذهب إلى SQL Editor في Supabase
2. شغل محتوى `database/schema.sql` مرة أخرى
3. تحقق من عدم وجود أخطاء في SQL

### خطأ: "Row Level Security"
**السبب**: مشاكل في صلاحيات قاعدة البيانات
**الحل**:
1. تأكد من تشغيل جميع RLS policies في schema.sql
2. تحقق من إعدادات Authentication في Supabase

### خطأ: "Module not found"
**السبب**: مشاكل في تثبيت التبعيات
**الحل**:
```bash
# حذف node_modules وإعادة التثبيت
rm -rf node_modules package-lock.json
npm install
```

### خطأ: "CORS error"
**السبب**: مشاكل في إعدادات CORS
**الحل**:
1. تأكد من إعداد Site URL في Supabase
2. تحقق من إعدادات Authentication

## نصائح للأداء والأمان

### الأمان
1. **لا تشارك مفاتيح API**: احتفظ بها سرية
2. **استخدم HTTPS**: في الإنتاج فقط
3. **فعل RLS**: تأكد من تفعيل Row Level Security
4. **كلمات مرور قوية**: للمستخدمين وقاعدة البيانات

### الأداء
1. **استخدم CDN**: لتحميل أسرع للملفات الثابتة
2. **ضغط الصور**: قلل حجم الصور المستخدمة
3. **Cache البيانات**: استخدم localStorage للبيانات المؤقتة
4. **تحسين SQL**: استخدم indexes للاستعلامات السريعة

## الدعم الفني

### الموارد المفيدة
- [Supabase Documentation](https://supabase.com/docs)
- [Bootstrap 5 Documentation](https://getbootstrap.com/docs/5.3/)
- [Vite Documentation](https://vitejs.dev/)

### الحصول على المساعدة
1. **GitHub Issues**: للمشاكل التقنية
2. **Supabase Discord**: للمساعدة في قاعدة البيانات
3. **Stack Overflow**: للأسئلة البرمجية العامة

---

**تهانينا!** 🎉 لقد أكملت إعداد نظام إدارة كراء الشقق اليومية بنجاح. يمكنك الآن البدء في استخدام النظام وتخصيصه حسب احتياجاتك.