OT Tracker Pro — Android project

এই ZIP হলো Android app source project, সরাসরি Play Console upload file নয়। GitHub Actions চালিয়ে signed Android App Bundle (.aab) তৈরি করতে হবে।

মোবাইল থেকে:
1. ZIP ডাউনলোড করে Extract করো।
2. github.com-এ sign in করে নতুন Private repository তৈরি করো।
3. Extract করা ফোল্ডারের ভেতরের সব ফাইল repository-র root-এ upload করো; ZIP-কে শুধু ZIP হিসেবেই upload কোরো না।
4. Actions tab খুলে "Build OT Tracker Pro AAB" workflow নির্বাচন করে Run workflow চাপো (প্রথম commit push করলেও workflow চলবে)।
5. সফল হলে Actions run-এর নিচে Artifacts থেকে OT-Tracker-Pro-SIGNED-AAB ডাউনলোড করো।
6. প্রথম build-এ OT-Tracker-Pro-PRIVATE-SIGNING-KEY artifact-ও থাকবে। এটি খুব গোপনীয়: .jks এবং signing-credentials.txt নিরাপদ জায়গায় রাখবে, কারও সঙ্গে শেয়ার করবে না। হারালে ভবিষ্যৎ update-এ একই signing key ব্যবহার করা কঠিন হতে পারে।
7. AAB-টি Play Console-এর testing release-এ আপলোড করার আগে পরীক্ষা করবে।

ভবিষ্যৎ update:
- একই signing key ব্যবহার করা জরুরি। GitHub repository Settings > Secrets and variables > Actions-এ OT_KEYSTORE_BASE64, OT_KEYSTORE_PASSWORD, OT_KEY_ALIAS, OT_KEY_PASSWORD secrets যোগ করতে হবে। release.jks ফাইলের Base64 বানাতে নিরাপদ কম্পিউটার/Termux পরিবেশ ব্যবহার করতে পারো; secret-গুলো কখনও public repository-তে রাখবে না।
- প্রথম build-এর keystore এবং credentials artifact কেবল 90 দিন থাকবে—সঙ্গে সঙ্গে নিজের নিরাপদ জায়গায় সংরক্ষণ করবে।

অ্যাপের সীমাবদ্ধতা:
- ডেটা ডিভাইসের WebView local storage-এ থাকে; অ্যাপ uninstall/clear data করলে ডেটা হারাতে পারে।
- বিজ্ঞাপন, subscription/payment, cloud sync বা secure admin login বাস্তবভাবে যুক্ত নেই; এগুলো demo UI হলে Play Store listing-এ live feature বলে দাবি কোরো না।
- প্রকাশের আগে privacy policy, Data safety form, app icon/screenshots, content rating, target audience এবং বাস্তব Android device-এ পরীক্ষা দরকার।
- Package ID: com.audora.ottrackerpro. প্রকাশের পরে এটি বদলালে update সমস্যা হবে।
- Target SDK 36 রাখা হয়েছে; 31 Aug 2026 থেকে নতুন অ্যাপের জন্য API 36 বা তার বেশি প্রয়োজন।
- Play Store approval নিশ্চিত নয়। Google-এর বর্তমান নীতিমালা এবং Play Console-এর সব সতর্কতা মেনে চলতে হবে।
