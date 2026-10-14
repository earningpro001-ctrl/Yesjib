# Job Prep BD (Android)

বাংলাদেশের চাকরিপ্রার্থীদের জন্য ফ্রি বাংলা UI-সহ MCQ প্রস্তুতি অ্যাপের Android Studio প্রজেক্ট।

## যা আছে
- বাংলা ড্যাশবোর্ড
- BCS, সরকারি চাকরি, ব্যাংক, প্রাথমিক শিক্ষক ও অন্যান্য চাকরির প্রস্তুতির বিভাগ
- বিষয়ভিত্তিক MCQ অনুশীলন
- মডেল টেস্ট মোড
- উত্তর যাচাই ও ব্যাখ্যা
- স্কোর রিপোর্ট এবং আগের ফলাফল
- ফলাফল ডিভাইসেই সংরক্ষণ (localStorage)

## APK বানানোর নিয়ম
এই পরিবেশে Android SDK/Gradle build tool নেই, তাই এখানে সরাসরি APK কম্পাইল করা সম্ভব হয়নি। এই ZIP-টি Android Studio-তে খুলে APK তৈরি করা যাবে।

1. কম্পিউটারে Android Studio ইনস্টল করুন।
2. Android Studio থেকে **Open** বেছে `JobPrepBD_Android_Project` ফোল্ডারটি খুলুন।
3. Gradle sync শেষ হওয়া পর্যন্ত অপেক্ষা করুন (প্রয়োজনে Android SDK 35 ইনস্টল করুন)।
4. **Build > Build Bundle(s) / APK(s) > Build APK(s)** নির্বাচন করুন।
5. তৈরি APK সাধারণত `app/build/outputs/apk/debug/app-debug.apk`-এ থাকবে।

## গুরুত্বপূর্ণ
- এটি প্রথম সংস্করণ/প্রোটোটাইপ। প্রশ্নগুলো নমুনা অনুশীলনী, অফিসিয়াল নিয়োগ পরীক্ষার প্রশ্ন বলে দাবি করা হচ্ছে না।
- চাকরির বিজ্ঞপ্তি ও লাইভ আপডেটের জন্য এখনো কোনো অনলাইন সার্ভার যুক্ত নেই।
- Play Store-এ প্রকাশের আগে অ্যাপটি বিভিন্ন ডিভাইসে পরীক্ষা, কনটেন্ট যাচাই এবং release signing করা উচিত।


## শুধু ফোন দিয়ে APK বানানোর সহজ পথ (GitHub Actions)

এই প্রজেক্টে `.github/workflows/build-apk.yml` রাখা হয়েছে। সোর্স ফাইল GitHub-এ আপলোড করে Actions চালালে ক্লাউডে APK তৈরি হবে। এটি নিজে থেকে কোনো APK তৈরি করে না।

1. ফোনের ব্রাউজারে https://github.com খুলে বিনামূল্যে অ্যাকাউন্ট তৈরি/লগইন করো।
2. নতুন একটি **Public repository** তৈরি করো, নাম দিতে পারো `JobPrepBD`।
3. ZIP ফাইলটি ফোনে Extract করো। GitHub repository-তে **Add file → Upload files** দিয়ে Extract করা প্রজেক্টের ফাইলগুলো ও `.github/workflows/build-apk.yml`-সহ ফোল্ডার কাঠামো আপলোড করতে হবে। শুধু ZIP ফাইলটিকে আপলোড করলেই বিল্ড হবে না.
4. আপলোড শেষে repository-র **Actions** ট্যাবে যাও। Workflow-টি চলতে শুরু করবে; না চললে **Build Job Prep BD APK → Run workflow** চাপো।
5. কাজ শেষ হলে সফল build খুলে **Artifacts** অংশ থেকে `JobPrepBD-debug-APK` ডাউনলোড করো।
6. ডাউনলোড করা ZIP-টি Extract করে `app-debug.apk` ফাইলটি চাপো। ফোন চাইলে Settings-এ ওই অ্যাপ/ব্রাউজারের জন্য **Install unknown apps** অনুমতি দিতে হবে।

সতর্কতা: APK-টি debug build হবে, Play Store-এ প্রকাশের জন্য প্রস্তুত signed release নয়। প্রথম বিল্ডে কোনো error হলে Actions-এর log থেকে error দেখে ঠিক করতে হবে.
