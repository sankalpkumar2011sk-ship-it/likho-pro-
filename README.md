# Likho Pro -- Professional Offline Android App

**Likho Pro** एक Android document editor है। इस repository में HTML editor
को Capacitor के जरिए Android APK में build करने के लिए project files और
GitHub Actions workflow दिया गया है।

## मुख्य सुविधाएँ

-   Offline HTML editor और local document storage
-   Android File Picker से फाइल Import
-   Android File Manager के `Open with` विकल्प के लिए intent filters
-   Save As के लिए Android document picker
-   Android Sharesheet से फाइल Share
-   PDF, DOC/DOCX, TXT, Markdown, HTML, RTF, PPT/PPTX और image MIME
    types के लिए file-opening integration
-   GitHub Actions से Debug APK build

> नोट: किसी format को Android के `Open with` में दिखाने के लिए MIME type और
> file manager का व्यवहार सही होना जरूरी है। फाइल खुलने और edit होने की क्षमता
> editor के importer/parser पर निर्भर करती है।

## GitHub repository बनाने की सेटिंग

Repository बनाते समय:

1.  Repository name: `likho-pro-android` (या अपनी पसंद का नाम)
2.  Visibility: **Public**
3.  `Add README`: OFF रख सकते हैं, क्योंकि यह README अलग से upload करेंगे।
4.  `.gitignore`: **Android** चुना जा सकता है।
5.  License: अपनी जरूरत के अनुसार चुनें। यदि आप नहीं चाहते कि दूसरे लोग आपका
    source code reuse करें, तो बिना समझे MIT License न चुनें।

Repository बनने के बाद project ZIP और workflow file upload करें।

## मोबाइल से ZIP और workflow upload करना

1.  इस project की ZIP file को GitHub repository में upload करें। ZIP का नाम
    बिल्कुल यह रखें: `Likho_Pro_Professional_Android_Project.zip`
2.  ZIP upload करने के बाद `Add file` → `Create new file` चुनें।
3.  नई file का path बिल्कुल यह रखें: `.github/workflows/build-apk.yml`
4.  Project ZIP के अंदर मौजूद `GITHUB_WORKFLOW_FOR_REPO.yml` खोलें और उसका
    पूरा content नई GitHub file में paste करें।
5.  `Commit changes` दबाएँ।
6.  Repository के **Actions** tab में `Build Likho Pro APK from ZIP`
    workflow खोलें। जरूरत हो तो `Run workflow` दबाएँ।
7.  Build पूरा होने के बाद सफल run खोलें। नीचे **Artifacts** में
    `Likho-Pro-Android-APK` डाउनलोड करें।
8.  Artifact ZIP को Android Files app में extract करें और `app-debug.apk`
    install करें।

## Repository में अपेक्षित फ़ाइलें

Repository root में ZIP file और workflow इस तरह होने चाहिए:

``` text
repository/
├── Likho_Pro_Professional_Android_Project.zip
└── .github/
    └── workflows/
        └── build-apk.yml
```

## APK build में इस्तेमाल

-   Capacitor 8
-   Node.js 22
-   Java 21
-   GitHub Actions Ubuntu runner
-   Android Gradle build (`assembleDebug`)

## Offline काम

Editor की local HTML, CSS और JavaScript APK में bundle होती हैं। इसलिए local
editor और device पर local data का काम internet के बिना चलना चाहिए।

इन कामों के लिए internet लग सकता है: - GitHub पर project upload करना और APK
build करना - कोई बाहरी website खोलना - Online sync या cloud backup (यदि
बाद में जोड़ा जाए) - HTML में जो external web links हों

## जरूरी सीमाएँ और परीक्षण

-   यह repository एक build template है; APK को वास्तविक Android फोन पर
    install करके जाँचना जरूरी है।
-   इस source package के लिए यहाँ Android SDK/Gradle build और
    physical-device testing नहीं की गई है। GitHub Actions का build log
    देखकर ही APK को सफल मानें।
-   PDF/DOCX/PPTX जैसे formats का पूरा layout support मौजूदा editor
    parser/export implementation पर निर्भर करता है। हर Microsoft Office
    document की 100% compatibility का दावा नहीं है।
-   Android file-opening integration में file size, MIME type, Android
    version और File Manager के व्यवहार से फर्क पड़ सकता है।
-   Native bridge में file size limit लागू हो सकती है; बहुत बड़ी files के लिए
    streaming support जोड़ना पड़ेगा।
-   Debug APK testing के लिए है। Release APK publish करने के लिए अलग signing
    key और release build configuration चाहिए। Signing key को GitHub
    repository में कभी upload न करें।

## समस्या आने पर

GitHub Actions में लाल ❌ दिखे तो:

1.  Failed workflow run खोलें।
2.  Failed step पर tap करें।
3.  पूरा error log या screenshot सुरक्षित रखें।
4.  Error log साझा करें ताकि सही कारण के अनुसार fix किया जा सके।

------------------------------------------------------------------------

**App name:** Likho Pro\
**Application ID:** `com.likhopro.app`
