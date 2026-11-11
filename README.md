# مساحة ياسمين

موقع عربي تعليمي عن الاستثمار، فيه بحث وتصنيفات وحفظ للمقالات ولوحة إدارة. الصفحة تعمل بفتح `index.html` مباشرة من الجهاز، من غير تثبيت حزم أو تشغيل خادم.

## الاستخدام

- لتجربة الموقع وتسجيل دخول الإدارة محليًا، شغّلي `npm start` ثم افتحي `http://localhost:4173`. لا تفتحي `index.html` مباشرة؛ تسجيل Firebase لا يعمل من عنوان `file://`.
- لتحديث نسخة النشر بعد تعديل المحتوى أو التصميم: شغّلي `npm run build`.

## النشر على GitHub Pages

بعد رفع المشروع إلى مستودع GitHub، اختاري **Settings → Pages → Build and deployment → GitHub Actions**. سير العمل الموجود في `.github/workflows/pages.yml` سيبني الموقع وينشره تلقائيًا عند كل تحديث لفرع `main`.

لتمكين تسجيل دخول الإدارة على رابط GitHub Pages، أضيفي نطاق `OWNER.github.io` إلى **Authentication → Settings → Authorized domains** في Firebase، مع استبدال `OWNER` باسم حساب GitHub. تبقى صلاحيات المقالات محكومة بقواعد Firestore الموجودة هنا.

## ربط فايربيز

1. فعّلي Firestore وEmail/Password في مشروع Firebase.
2. أضيفي إعدادات Web App في `firebase-config.js`، ثم شغّلي `npm run build` وافتحي `index.html` مجددًا.
3. انشري `firestore.rules` وملفات الموقع بـ `firebase deploy`.
4. أضيفي حساب الإدارة في Authentication، وأنشئي مستندًا فارغًا في مجموعة `admins` بمعرّف UID الخاص به.
5. من لوحة الإدارة سجّلي الدخول واختاري «استيراد المحتوى التعليمي» لإضافة المقالات الافتتاحية إلى Firestore.

المقالات متاحة للقراءة العامة، وتقتصر عمليات الإضافة والتعديل والحذف على من له مستند في مجموعة `admins`. لا تضعي مفاتيح Admin SDK في ملفات الموقع.

