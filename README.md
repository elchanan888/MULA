# מנהל חנות WooCommerce — PWA

ממשק בעברית לניהול מוצרים, קטגוריות, הזמנות ונתוני מכירות. החבילה מיועדת לפרסום ישיר ב-GitHub Pages.

## פרסום ב-GitHub Pages

1. חלץ את קובץ ה-ZIP.
2. העלה את **כל הקבצים** שבתיקייה למאגר GitHub. חשוב לשמור על מבנה התיקיות.
3. ודא שבאותה תיקיית פרסום נמצאים `index.html`, `manifest.webmanifest`, `sw.js` ותיקיית `icons`.
4. ב-GitHub פתח Settings → Pages, בחר את הענף ואת תיקיית הפרסום ושמור.
5. פתח את האתר בכתובת HTTPS. בדפדפן נתמך תוצג אפשרות התקנה; אפשר גם להשתמש בתפריט הדפדפן ולבחור Install app / הוסף למסך הבית.

## ייבוא הגדרות — בלי להקליד שדה אחר שדה

במסך **הגדרות וחיבור → ייבוא וייצוא הגדרות** אפשר:

- לבחור קובץ `.json`, `.txt`, `.env`, `.cfg` או `.ini` מהמכשיר.
- לגרור קובץ לאזור הייבוא.
- להדביק JSON או טקסט בתיבה.
- ללחוץ על **הדבקה מהלוח** כדי לטעון טקסט שהועתק.
- אחרי טעינת הקובץ/ההדבקה, ללחוץ **ייבוא ושמירה**. אפשר להפעיל בדיקת חיבור אוטומטית לאחר הייבוא.
- לייבא רק חלק מהשדות; שדות שלא נכללו נשארים ללא שינוי.

קובץ שנבחר נקרא **מקומית בדפדפן בלבד** — הוא לא מועלה לשרת. התוכן נטען לתיבה כדי שאפשר יהיה לבדוק אותו לפני שמירתו.

## מבנה JSON מומלץ

```json
{
  "storeUrl": "https://example.co.il",
  "consumerKey": "ck_...",
  "consumerSecret": "cs_...",
  "wpUsername": "wordpress-user",
  "wpAppPassword": "xxxx xxxx xxxx xxxx xxxx xxxx"
}
```

אפשר גם להשתמש במבנה מקונן:

```json
{
  "woocommerce": {
    "url": "https://example.co.il",
    "key": "ck_...",
    "secret": "cs_..."
  },
  "wordpress": {
    "username": "wordpress-user",
    "password": "xxxx xxxx xxxx xxxx xxxx xxxx"
  }
}
```

במבנה השני, `wordpress.password` מתפרש כ-**Application Password**. אין לייבא שם את סיסמת ההתחברות הרגילה.

## שמות שדות נתמכים

| מידע | מפתחות לדוגמה |
|---|---|
| כתובת החנות | `storeUrl`, `store_url`, `siteUrl`, `site_url`, `url`, `woocommerce_url`, `wp_url` |
| WooCommerce Consumer Key | `consumerKey`, `consumer_key`, `ck`, `woocommerce_key`, `woocommerce_consumer_key` |
| WooCommerce Consumer Secret | `consumerSecret`, `consumer_secret`, `cs`, `woocommerce_secret`, `woocommerce_consumer_secret` |
| שם משתמש WordPress | `wpUsername`, `wp_username`, `wordpress_username`, `wordpress_user`, `username` |
| סיסמת יישום WordPress | `wpAppPassword`, `wp_app_password`, `wp_application_password`, `wordpress_app_password`, `wordpress_password`, `wpPassword`, `application_password` |

בטקסט ENV או שורות `KEY=VALUE` / `KEY: VALUE` אפשר להשתמש למשל כך:

```text
STORE_URL=https://example.co.il
CONSUMER_KEY=ck_...
CONSUMER_SECRET=cs_...
WP_USERNAME=wordpress-user
WP_APP_PASSWORD=xxxx xxxx xxxx xxxx xxxx xxxx
```

אפשר גם להשתמש בכותרות מקטע `[woocommerce]` ו-`[wordpress]`.

## הרשאות וחיבור

- `consumerKey` ו-`consumerSecret` הם מפתחות WooCommerce API לניהול מוצרים, קטגוריות, הזמנות ודוחות. צור אותם דרך WooCommerce → Settings → Advanced → REST API, עם הרשאת Read/Write ומשתמש בעל הרשאות מתאימות.
- `wpUsername` ו-`wpAppPassword` מיועדים לאימות WordPress REST API, בעיקר להעלאת תמונות למדיה. Application Password נוצרת בפרופיל המשתמש ב-WordPress. היא אינה סיסמת הכניסה הרגילה ואינה מחליפה את מפתחות WooCommerce.
- אם מתקבלת שגיאת 401/403, האפליקציה משהה את הסנכרון האוטומטי כדי למנוע לולאת בקשות. לאחר תיקון המפתחות יש לבצע בדיקת חיבור ידנית.
- שגיאות CORS או הסרת כותרת Authorization עשויות להצריך שינוי בתצורת שרת WordPress / Proxy / תוסף אבטחה. אין לחשוף מפתחות בכתובות URL.

## תכונות

- מסך בית עם סיכום מכירות והזמנות לשבעת הימים האחרונים, ממוצע להזמנה, הזמנות פתוחות וחמש הזמנות אחרונות.
- מסך סטטיסטיקות מלא עם דוחות מכירות, מגמה יומית, מוצרים מובילים וסטטוס הזמנות.
- ניהול מוצרים, מק"ט, תמונות וקטגוריות.
- צפייה בהזמנות, סינון, פרטים, עדכון סטטוס וייצוא CSV.
- ממשק בעברית ו-RTL, רספונסיבי, עם סט אייקוני SVG אחיד.

## PWA ומצב לא מקוון

החבילה כוללת `manifest.webmanifest`, `sw.js` ואייקונים בגודל 192 ו-512 פיקסלים. ה-Service Worker משתמש במטמון מעטפת חדש (`wc-manager-shell-v3`) ומוחק מטמונים קודמים של מנהל החנות. הוא **אינו** שומר תשובות API, פרטי לקוחות, הזמנות או פרטי אימות. ניתן להציג את מעטפת האתר במצב לא מקוון לאחר טעינה ראשונה; כל קריאה או שינוי בחנות דורשים אינטרנט.

## פרטיות ואבטחה

פרטי החיבור נשמרים ב-LocalStorage של הדפדפן שבו הוזנו. אין backend או הצפנה של המפתחות בקובץ זה. קובצי ייצוא כוללים סודות — אין לשמור אותם במאגר ציבורי, לשלוח אותם בצ'אט ציבורי או להשתמש במפתחות מנהל במחשב משותף. לשימוש רב-משתמשים או עסקי רגיש מומלץ שרת מתווך מאובטח.

## בדיקות שבוצעו בגרסה זו

בדיקות תחביר JavaScript; בדיקת מזהי DOM כפולים והפניות חסרות; בדיקת תבניות JSON, ENV, JSON מקונן וקובץ; בדיקות דפדפן עם API מדומה לטעינת מוצרים/קטגוריות/הזמנות/דוחות, יצירת מוצר, עריכת מוצר, יצירת קטגוריה ועדכון סטטוס הזמנה; בדיקת עצירת ניסיונות רקע לאחר 401; בדיקת רוחב מסך 390px ובדיקת אייקוני SVG.

הבדיקות השתמשו בנתוני API מדומים ואינן מהוות בדיקת חיבור חי לחנות מסוימת.
