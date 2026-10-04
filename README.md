# تطبيق رصد الغياب – مدرسة بلال بن رباح (أندرويد + آيفون)

مشروع [Capacitor](https://capacitorjs.com) يغلّف برنامج رصد الغياب
`https://akmoman.github.io/bilal2/` داخل تطبيق أصلي واحد يعمل على أندرويد وiOS.
أي تحديث تنشره على الموقع يظهر تلقائيًا في التطبيق دون إعادة نشره في المتاجر.

## المتطلبات
- Node.js 18 أو أحدث
- للأندرويد: Android Studio
- للآيفون: جهاز Mac مع Xcode وحساب Apple Developer (99$ سنويًا)
- للأندرويد على متجر Google Play: حساب مطوّر (25$ مرة واحدة)

## الخطوات

```bash
cd bilal-app
npm install

# أندرويد
npm run add:android
npm run sync
npm run open:android     # يفتح Android Studio ← Build > Generate Signed Bundle / APK

# آيفون (على جهاز Mac فقط)
npm run add:ios
npm run sync
npm run open:ios         # يفتح Xcode ← Product > Archive
```

## الأيقونة وشاشة البداية
ضع صورة `assets/icon.png` (1024×1024) و`assets/splash.png` (2732×2732) ثم نفّذ:

```bash
npx capacitor-assets generate
```

## ملاحظات مهمة
1. **الاتصال بالإنترنت مطلوب**: التطبيق يعرض الموقع مباشرة، وتظهر صفحة `offline.html` عند انقطاع الاتصال.
2. **قبول متجر Apple**: Apple قد ترفض التطبيقات التي هي مجرد غلاف لموقع (البند 4.2). لتقليل الخطر أضف وظائف أصلية
   (إشعارات، تخزين محلي، دعم عمل دون اتصال) أو وزّع التطبيق عبر TestFlight / التوزيع الداخلي للمدرسة.
3. **أندرويد**: يمكنك أيضًا توزيع ملف APK مباشرة داخل المدرسة دون المرور بالمتجر.
4. معرّف التطبيق `om.akmoman.bilal.attendance` يمكن تغييره في `capacitor.config.json` قبل أول إضافة للمنصات.
5. إذا كان البرنامج يحفظ البيانات في المتصفح (localStorage)، فستبقى داخل التطبيق ما دام نفس النطاق مستخدمًا.
