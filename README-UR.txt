WASIF PRIVATE CHAT — SETUP

1) Firebase Console (https://console.firebase.google.com/) میں اپنے project my-chat-app-b9b0e کو کھولیں۔
2) Authentication > Sign-in method میں Phone provider کو Enable کریں۔
3) Authentication > Settings میں SMS region policy میں Pakistan (+92) کی اجازت دیں۔ SMS quota/billing اور Google کی verification requirements لاگو ہو سکتی ہیں۔ پہلے test phone numbers استعمال کر سکتے ہیں۔
4) Firestore Database بنائیں (Production mode)۔
5) Firestore Database > Rules میں firestore.rules کا پورا متن paste کرکے Publish کریں۔
6) index.html کو HTTPS hosting پر چلائیں (Firebase Hosting تجویز ہے)۔ صرف فائل کو file:// سے کھولنے پر فون OTP/reCAPTCHA درست نہ چلنے کا امکان ہے۔
7) دونوں افراد اپنی اپنی ڈیوائس پر ویب سائٹ کھولیں، اپنے اپنے فون نمبر پر OTP سے login کریں، پھر دوسرے شخص کا نمبر +92 فارمیٹ میں درج کرکے "پرائیویٹ چیٹ کھولیں" دبائیں۔
8) دونوں کا نمبر بالکل ایک جیسا international format میں ہونا چاہیے، مثلاً +923001234567۔

اہم:
- index.html میں Firebase config پہلے سے آپ کے فراہم کردہ کوڈ سے بھرا ہوا ہے۔
- Firebase web apiKey عام طور پر public config ہوتی ہے؛ اسے secret نہ سمجھیں۔ اصل تحفظ Firestore Rules، Phone Authentication، اور Firebase project restrictions سے آتا ہے۔
- اس starter app میں صرف text messages ہیں۔ یہ WhatsApp جیسی end-to-end encrypted service نہیں ہے؛ Firebase project owner/backend access رکھنے والا ڈیٹا دیکھ سکتا ہے۔ حساس گفتگو کے لیے اسے production security review اور حقیقی E2EE design کے بغیر استعمال نہ کریں۔
- Phone OTP کے لیے Firebase کی limits، allowed regions، SMS billing/quotas اور reCAPTCHA درکار ہو سکتے ہیں۔
- اگر آپ پہلے سے Firestore میں rooms collection رکھتے ہیں تو اس نام کے rules پر اثر پڑ سکتا ہے؛ publish کرنے سے پہلے اپنے موجودہ rules کا backup لیں۔
- friend number پہلی بار درج کرنے والا room document بناتا ہے؛ دوسرا شخص اپنے اسی phone number سے login کرکے وہی friend number درج کرے گا تو اسی room میں داخل ہوگا۔
