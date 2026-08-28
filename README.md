# RAS Pre Quiz App — स्वयं-निर्मित सिलेबस

## GitHub Pages पर Deploy कैसे करें (Step by Step)

### Step 1 — GitHub Account बनाएं
1. https://github.com पर जाएं
2. Sign Up करें (Free account)

### Step 2 — New Repository बनाएं
1. GitHub पर Login करें
2. ऊपर **"+"** बटन → **"New repository"** क्लिक करें
3. Repository name: `ras-pre-quiz` (या कोई भी नाम)
4. **Public** चुनें
5. **"Create repository"** क्लिक करें

### Step 3 — Files Upload करें
1. Repository खुलने के बाद **"uploading an existing file"** क्लिक करें
2. इन 5 फाइलों को drag-and-drop करें:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
3. **"Commit changes"** क्लिक करें

### Step 4 — GitHub Pages Enable करें
1. Repository में **Settings** → **Pages** जाएं
2. Source: **"Deploy from a branch"**
3. Branch: **main** → **/ (root)**
4. **Save** क्लिक करें
5. 2-3 मिनट में आपका URL मिलेगा:
   `https://[आपका-username].github.io/ras-pre-quiz/`

---

## नया Feature — सिलेबस आप खुद बनाते हैं

पुरानी RPSC 1st Grade app में पूरा सिलेबस पहले से कोडेड था। इस RAS Pre app में **"📚 सिलेबस प्रबंधन"** नाम का नया टैब है, जहाँ आप खुद:

1. **Subject जोड़ें** — जैसे "राजस्थान का इतिहास एवं संस्कृति" (Icon भी चुन सकते हैं)
2. **उसमें Micro-topic जोड़ें** — जैसे "1857 की क्रांति"
3. **हर Micro-topic का वेटेज डालें** — यानी RAS Pre में उस टॉपिक से औसतन कितने प्रश्न आते हैं (जैसे `1.5`)

शुरुआत में 9 मुख्य Subject के नाम पहले से जोड़ दिए हैं (RAS Pre pattern के अनुसार — जैसे राजस्थान इतिहास, भूगोल, राजव्यवस्था, अर्थव्यवस्था, समसामयिकी आदि) ताकि आपको Subject बनाने से शुरुआत न करनी पड़े। इनमें कोई Micro-topic नहीं है — वो आप खुद जोड़ेंगे। आप चाहें तो इन्हें rename/delete भी कर सकते हैं, और नए Subject भी जोड़ सकते हैं।

### वेटेज किस काम आता है?
- हर टॉपिक पर 🔥 उच्च (≥1.5) / ⚡ मध्यम (≥0.5) / 💡 कम बैज दिखता है
- **Mock Test** में "वेटेज के अनुसार प्रश्न चुनें" विकल्प चुनने पर ज़्यादा वेटेज वाले टॉपिक से अपने-आप ज़्यादा प्रश्न शामिल होंगे — असली परीक्षा पैटर्न जैसा अभ्यास

### सिलेबस Import/Export (Backup)
"सिलेबस प्रबंधन" टैब में **Export** बटन से पूरा सिलेबस (सभी Subject + Topic + वेटेज) एक JSON फाइल में डाउनलोड हो जाता है — इसे बैकअप रखें, या दूसरे device पर **Import** करें।

---

## App का उपयोग

### JSON Format (प्रश्न कैसे बनाएं)
```json
[
  {
    "q": "यहाँ प्रश्न लिखें",
    "o": ["विकल्प A", "विकल्प B", "विकल्प C", "विकल्प D"],
    "a": 1,
    "exp": "व्याख्या (वैकल्पिक)",
    "src": "RAS Pre 2023 (वैकल्पिक)",
    "diff": "medium"
  }
]
```
- `a` = सही उत्तर index: 0=A, 1=B, 2=C, 3=D
- `diff` = "easy" / "medium" / "hard"

### प्रश्न अपलोड करने का तरीका (2 कदम)
1. पहले **"📚 सिलेबस प्रबंधन"** में जाकर Subject + Micro-topic (वेटेज सहित) बनाएं
2. फिर **"⚙️ प्रश्न प्रबंधन"** टैब में उस टॉपिक को dropdown से चुनें और JSON पेस्ट करें, या `.json` फाइल drag-and-drop करें

### Data कहाँ सेव होता है?
- सिलेबस, प्रश्न, और प्रगति — सब आपके **Browser के LocalStorage** में सेव होते हैं
- Internet बंद होने पर भी काम करता है (PWA/Offline)
- **एक device पर बनाया गया सिलेबस/प्रश्न = उसी device पर दिखेगा**, जब तक Cloud Sync ना जोड़ें

### सभी devices पर sync करने के लिए (Cloud Sync)
App में ही **"☁️ Cloud Sync"** टैब में पूरी Step-by-Step guide दी गई है (Supabase — मुफ़्त सेवा)। इसमें सिलेबस और प्रश्न दोनों एक साथ sync होते हैं — अलग से कोई कोड जोड़ने की ज़रूरत नहीं।

---

## ऐप के सभी Features
| Feature | विवरण |
|---|---|
| 📚 सिलेबस प्रबंधन | खुद Subject/Micro-topic/वेटेज बनाएं |
| ⚙️ प्रश्न प्रबंधन | हर टॉपिक में JSON प्रश्न अपलोड करें |
| 🎮 Quiz | किसी भी Micro-topic का अभ्यास (Practice/Test मोड) |
| 🏆 Mock Test | पूरे सिलेबस से, वेटेज के अनुसार, समय-सीमा के साथ |
| 📊 कमज़ोर टॉपिक्स | सबसे कम सटीकता वाले टॉपिक अपने-आप ऊपर दिखें |
| 📕 Revision Bank | गलत किए गए प्रश्न अपने-आप जुड़ें, बार-बार दोहराएं |
| 📌 Bookmarks | ज़रूरी प्रश्न सेव करें |
| 🎯 Daily Target | रोज़ाना लक्ष्य + Streak tracking |
| 📈 प्रगति | विषयवार सटीकता व प्रश्न-संख्या |
| ☁️ Cloud Sync | सभी devices पर सिलेबस+प्रश्न sync (Supabase, मुफ़्त) |
