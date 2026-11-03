# WooCommerce Manager PWA

## פרסום ב-GitHub Pages
1. העלה את כל התוכן שבתיקייה הזו למאגר GitHub (לא רק את index.html).
2. ודא ש-`index.html`, `manifest.webmanifest`, `sw.js` ותיקיית `icons` נמצאים יחד בתיקיית הפרסום.
3. ב-GitHub: Settings → Pages → בחר את הענף והתיקייה שבהם נמצאים הקבצים.
4. פתח את כתובת GitHub Pages ב-HTTPS. בדפדפן נתמך תופיע אפשרות התקנה; אפשר גם לבחור בתפריט הדפדפן "Install app".

## ייבוא הגדרות
במסך הגדרות ניתן להדביק JSON או טקסט בפורמט:

```text
STORE_URL=https://example.co.il
CONSUMER_KEY=ck_...
CONSUMER_SECRET=cs_...
WP_USERNAME=wordpress-user
WP_APP_PASSWORD=xxxx xxxx xxxx xxxx xxxx xxxx
```

## אבטחה ופרטיות
פרטי החיבור נשמרים ב-LocalStorage בדפדפן. ייצוא הגדרות כולל סודות; שמור את קובץ הייצוא במקום מאובטח ואל תעלה אותו ל-GitHub. ה-Service Worker שומר רק את מעטפת האפליקציה והאייקונים ואינו שומר בקשות API או מידע הזמנות.

## מצב לא מקוון
ניתן לפתוח את מעטפת הממשק ללא חיבור לאחר טעינה ראשונה. קריאת/עריכת מוצרים, הזמנות, תמונות ונתוני מכירות דורשת חיבור אינטרנט ושרת WooCommerce זמין.
