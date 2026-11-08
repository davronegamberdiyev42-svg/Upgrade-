# IELTS Boost Stage 36 — yakuniy QA hisoboti

**Release:** 36.0.0  
**Sana:** 2026-11-07  
**Maqsad:** 84 kunlik IELTS platformasini saqlagan holda 10 ta ilg‘or daily mission, Speaking transcript/tahlili, 10 × 10 Power Labs, vocabulary lookup va Android PWA tayyorgarligini kuchaytirish.

## Avtomatik tekshiruvlar

| Tekshiruv | Natija | Izoh |
|---|---|---|
| Asosiy JavaScript sintaksisi | PASS | `node --check` |
| Service Worker sintaksisi | PASS | `node --check sw.js` |
| Embedded `appData` JSON | PASS | Parse qilindi; 84 kunlik ma’lumot saqlandi |
| `manifest.webmanifest` | PASS | JSON parse; `display: standalone`, `start_url`, `scope` mavjud |
| Stage 36 logic harness | PASS | 8/8 test: radio selection, exact evidence, NOT GIVEN absence, Listening source match, Speaking analysis |
| 10 ta daily mission | PASS | Reading, Listening, Writing, Speaking va 6 lab sahifasi ochildi; har birining submit/result oqimi sinovdan o‘tdi |
| Eski Power Labs | PASS | 10 modul × 10 rejim = 100 rejim navigatsiyasi tekshirildi |
| Speaking report va TXT eksport | PASS | Hisobot render bo‘ldi, to‘rt mezonli self-review hisoblandi, `.txt` download ishladi |
| ASR event integratsiyasi | PASS (mock) | Soxta `SpeechRecognition` callback transcriptni maydonga kiritdi va hisobot tuzildi; bu haqiqiy mikrofon testi emas |
| ASR ruxsat xatosi fallback | PASS | Ruxsat berilmaganda foydalanuvchiga manual transcript yo‘li ko‘rsatildi |
| Mobil layout | PASS | 390px viewport’da JS page error va gorizontal overflow topilmadi |
| Audio decode | PASS | 84/84 MP3 `ffmpeg` bilan decode qilindi |
| Ikonkalar | PASS | `icon-192.png` va `icon-512.png` mavjud |
| To‘liq ZIP yaxlitligi | PASS | `ZipFile.testzip()` xatosiz |
| Root / icon / 3 audio split ZIP | PASS | Barcha komponent arxivlari integrity testdan o‘tdi |

## Hajm va GitHub upload

- `index.html`: 15,924,816 bytes (15.19 MiB).
- Audio: 84 MP3, jami 57,539,664 bytes (54.87 MiB); eng kattasi 769,100 bytes.
- GitHub uchun bitta ZIP’ni yuklash emas, ZIP’larni telefonda Extract qilib, ichidagi fayllarni joylashtirish ko‘zda tutilgan.
- `01_Root_Files.zip` — ilova va PWA root fayllari; `02_Icons.zip` — 2 ta PNG; `03–05_Audio` — 28 tadan MP3.

## Vocabulary — aniq sonlar va cheklov

- Birinchi 10,000 searchable entry: 10,000; noyob word form: 10,000.
- US + UK IPA maydoni mavjud: 10,000/10,000. IPA yozuvlari inherited index’dan olingan; ayrimlari avtomatik hosil qilingan bo‘lishi mumkin, shuning uchun learner dictionary audio bilan tekshirish tavsiya etiladi.
- To‘liq offline glossary (English definition + Uzbek meaning + example + part of speech): **671/10,000**.
- Shu release’ni **9,000 ta tayyor offline definition yoki 4,000 ta tekshirilgan Uzbek tarjima bor** deb ko‘rsatish mumkin emas. Qolgan so‘zlarga definition/translation API orqali alohida online lookup berilgan; internet, API availability, quota, CORS va machine translation sifati kafolatlanmaydi.

## Speaking — nimalar ishlaydi va nimalar emas

- MediaRecorder yozuvlari mavjud eski oqim bilan saqlanadi; Stage 36 recording boshlanganida browser SpeechRecognition mavjud bo‘lsa, live transcriptni ham yoqadi.
- Manual transcript maydoni va `.txt` eksport fallback sifatida bor.
- Hisobot: word/sentence count, average sentence length, unique-token ratio, fillers, discourse marker signals, clause signals, repeated content words, ehtimoliy grammar patternlar, Part 1/2/3 breakdown va 4 mezonli learner self-review.
- Transcript tahlili heuristic hisoblanadi. U accent, intelligibility, stress, intonation yoki talaffuzni avtomatik tekshirmaydi; pronunciation audio qayta tinglash va evidence/self-review talab qiladi.
- 0–10 ko‘rsatkichlar ichki practice score; rasmiy IELTS band yoki examiner score emas.

## Hali qurilmada tasdiqlanishi shart

1. Samsung Galaxy A14’da haqiqiy microphone permission, MediaRecorder va live SpeechRecognition.
2. GitHub Pages HTTPS’da Service Worker activation/update va first load/offline shell.
3. Android Chrome’da haqiqiy `Install app` prompt va address bar’siz standalone launch. Faqat `Add to Home screen` chiqishi shortcut bo‘lishi mumkin.
4. IndexedDB audio recording’lar reload’dan keyin tiklanishi va oldingi progress migration.
5. Dictionary va translation API’lar real tarmoqda ishlashi.

**Bu bandlar sandbox’da PASS deb belgilanmadi.** PWA haqiqiy install va Android microphone sinovini qurilmada bajarish kerak.

## Manba va copyright siyosati

84 audio — IELTS Boost uchun yaratilgan synthetic practice audio; rasmiy IELTS/Cambridge/British Council yozuvi emas. Kundalik Reading/Writing/Speaking materiallar original practice. Rasmiy IELTS, Cambridge, Collins va Barron’s manbalari format/mezonga yo‘l-yo‘riq hamda qonuniy access linki sifatida keltiriladi; pullik kitoblarning himoyalangan to‘liq matni, audiosi yoki answer key’i qayta tarqatilmaydi.
