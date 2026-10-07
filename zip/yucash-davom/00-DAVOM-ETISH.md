# YuCash: suhbat xulosasi (yangi oynada davom etish uchun)

Yangi suhbatda shu papkani (zip) yuklab, "shu yerdan davom etamiz" deb yozing.
Batafsil yozishmalar tarixi: `01-YOZISHMALAR.md`.

## Loyiha
- Ilova nomi: **YuCash**, o'zbekcha interfeys. Endi **xarajatlarni ovoz bilan yozib, toifalarga avtomatik ajratadigan** ilova (avval harakat sanagich edi).
- 5 bo'lim (o'ngga/chapga suriladi): Asosiy (kunlik xarajat halqasi, mikrofon, yozuv maydoni, saqlashdan oldingi tasdiq kartasi), Dashboard (Bugun/7 kun/Jami so'mda, 7 kunlik grafik, toifalar), Tarix, Obuna (demo: Bepul / Pro oylik 19 000 / Pro yillik 149 000 so'm, haqiqiy to'lov yo'q), Sozlamalar (kunlik limit, mavzu, ovoz tili, versiya + "Yangilash", ma'lumotni o'chirish).
- Ma'lumot telefonning localStorage'ida, kalit: `yucash2` (eski `yucash` harakat yozuvlari ishlatilmaydi).
- Bitta HTML fayl, PWA: `ilova-fayllari/` ichida index.html, sw.js, manifest.json, icon-192.png, icon-512.png, README.md.

## Ovozli kiritish (hozirgi versiya: v5)
- Web Speech API (`webkitSpeechRecognition`), til `S.lang` (uz-UZ / uz / ru-RU, Sozlamalarda tanlanadi), 5 ta variant olinadi, summasi aniqlanganini tanlaydi.
- `fixUz()`: turkcha harflar (ş ç ğ ı ö ü) va kirill yozuvi o'zbekcha lotinga o'giriladi. Bunga sabab: tanish dvigateli o'zbekchani turkcha yozib chiqarardi.
- `parseAmt()`: raqamlar ("45 000", "25 ming") va so'zlar ("yigirma besh ming", turkcha "yirmi beş bin" ham) summaga aylanadi; gapdagi eng katta son summa deb olinadi. Sinab ko'rilgan: 25 000, 15 000, 50 000, 120 000, 1 200 000, 45 000.
- `catOf()`: kalit so'zlar bo'yicha toifa: Oziq-ovqat, Kafe, Transport, Kommunal, Salomatlik, Kiyim, Ko'ngilochar, Ta'lim, Boshqa.
- Eshitilgach tasdiq kartasi chiqadi: summa va toifani o'zgartirib "Saqlash".
- Mikrofon ishlamasa: yozuv maydoniga "taksi 25 ming" yozish yoki klaviaturadagi (Gboard) mikrofon.
- Mikrofon bosqichlari tugma ostida ko'rinadi ("Tayyorlanmoqda…", "Tinglayapman…") va xato kodi chiqadi (`[not-allowed]`, `[network]`, `[service-not-allowed]`, `[language-not-supported]`, `[audio-capture]`, `[no-speech]`). 4 soniyada ishga tushmasa o'zi to'xtaydi.

## Versiyalar tarixi
- v2: ovozli xarajat yozuvi birinchi marta qo'shildi.
- v3: turkcha/kirill tuzatish, ovoz tili tanlovi, versiya raqami va "Yangilash" tugmasi. Muammo: mikrofon bosilganda tinglamadi.
- v4: ruxsat tekshiruvi, bosqichlar, xato kodlari, 4 soniyalik taymer. Muammo: mikrofon bosilganda yozuv maydoniga o'tib ketardi (oldindan ruxsat tekshiruvi rad etilgani uchun).
- v5: oldindan tekshiruv endi to'sqinlik qilmaydi, yozuv maydoni o'zi ochilmaydi. Fayllar tayyor, **hali telefonda sinalmagan**.
- Har versiyada `sw.js` ichidagi kesh nomi oshiriladi (`yucash-v5`), shunda yangilanish ilovaga yetib boradi.

## Hozirgi holat
- GitHub: `https://github.com/hopbeats59-collab/yucash`, sayt: `https://hopbeats59-collab.github.io/yucash/`. APK pwabuilder orqali yasalgan va tayyor (foydalanuvchi aytdi). APK sayt havolasidan yuklanadi, shuning uchun saytni yangilasak ilova ham yangilanadi, APK'ni qayta yasash shart emas.
- Termux'da loyiha `~/yucash` papkasida. Foydalanuvchi fayllarni telefonga yuklab oladi (`~/storage/downloads/`).
- v5 ni joylash (keyingi qadam, bittadan beriladi):
  1. `cp ~/storage/downloads/index.html ~/storage/downloads/sw.js ~/yucash/`
  2. `cd ~/yucash`
  3. `git add .`
  4. `git commit -m "v5"`
  5. `git push` (Username: hopbeats59-collab, Password: token). Index.html `~/yucash` ildizida ekanini tekshirish kerak (agar `ilova-fayllari` ichida bo'lsa, shu yerga nusxalash).
- Ilovada Sozlamalar -> "Versiya 5" ko'rinsa, yangilanish yetib kelgan. Eski chiqsa, "Yangilash" tugmasini bosish.

## Ochiq masala
- APK ichida mikrofon: v5 sinab ko'riladi. Foydalanuvchi mikrofonni bosgach tugma ostida chiqqan yozuvni (kod bilan) yozib yuboradi; shunga qarab sabab topiladi.
- Telefonda Google ovozli yozuvga o'zbek tili qo'shilgan bo'lishi kerak (Sozlamalar -> Google -> Ovozli kiritish / Gboard -> Tillar -> O'zbek).
- Agar APK ichida ovoz tanish umuman ishlamasa: asosiy yo'l klaviatura mikrofoni, yoki ilovani Chrome'da ochish.

## Foydalanuvchi uchun eslatmalar
- Foydalanuvchi o'zbekcha yozadi, yangi boshlovchi: bitta qadam, bitta buyruq beriladi, qisqa tushuntiriladi.
- Foydalanuvchi har bir o'zgarishni ilovaning o'zida sinab ko'rmoqchi: har o'zgarishda versiya raqamini oshirish va qadamlarni sodda berish kerak.
- Termux'da faqat buyruqning o'zini yozish kerak (`~/yucash $` belgisini emas).
- Tokenni hech kimga yubormaslik kerak. Bu papkada token yo'q.
