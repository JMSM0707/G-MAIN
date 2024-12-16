# G-MAIN
# 🔹Grass Auto ro'yhatdan o'tish va point farm 🔹

NODE

![image](github.com/JMSM0707/G-MAIN/blob/main/core/static/Image-2.png)

### Bot nima qila oladi?
   - Akkaunt yaratadi
   - Farm Point
   - Pointlarni tekshiradi
   - Kirishni imkoni bo'lmagan elektron pochta xabarlarini tasdiqlaydi (imap kerak emas va hokazo)

> Siz imkon qadar ko'proq proksi-server qo'yishingiz mumkin, bot ma'lumotlar bazasidan foydalanadi va proksi-serverlarni qo'shimcha proksilardan yuklaydi.


1 akkauntga bir nechta ulanishlarni ulash uchun akkauntlarni accounts.txt faylida ko'paytirish kifoya.

## Tez boshlash 📚
   1. Windows-da kutubxonalarni o'rnatish uchun `INSTALL.bat` tugmasini bosing (yoki konsolda: `pip install -r requirements.txt`).
   2. Botni ishga tushirish uchun `START.bat` (yoki konsolda: `python main.py`) dan foydalaning.

### Variantlar 📧

1. AKKAUNT YARATISH:
 - `data/config.py` da `REGISTER_ACCOUNT_ONLY = True` so'zini qo'ying
 - Api kalitini "data/config.py" ga joylang. Ro'yhatdan o'tish uchun captcha so'ralgani uchun, sizga captchalarni hal qilish uchun xizmat kerak bo'ladi - [AntiCaptcha](http://getcaptchasolution.com/t8yfysqmh3) or [Twocaptcha](https://2captcha.com/?from=12939391).
 - Hisob qaydnomalarini ro'yxatdan o'tkazish uchun quyidagi tarzda elektron pochta va parollar (ixtiyoriy) va proksi-serverlarni taqdim eting!



2. FARM POINT:
 - `data/config.py` da `REGISTER_ACCOUNT_ONLY = False` so'zini qo'ying
 - Yuqorida ko'rsatilganidek, hisoblarni elektron pochta va parollar va proksi-serverlarni taqdim eting!

3. E-Pochta XATLARINI TASDIQLASH:
 - "data/config.py" da:
   - `APPROVE_EMAIL = True` e-pochtani tasdiqlang (IMAP VA E-Pochtaga kirish KERAK)
   - `CONNECT_WALLET = True` hamyonni ulash (shaxsiy kalitlarni wallets.txt-ga joylashtiring)
   - `SEND_WALLET_APPROVE_LINK_TO_EMAIL = True`  # tasdiqlash havolasini elektron pochtaga yuboring
   - `APPROVE_WALLET_ON_EMAIL = True`  # elektron pochtadan ma'qullash havolasini oling (IMAP VA E-Pochtaga kirish KERAK)
 - Email:password:imap_password formatida elektron pochta va parol hamda imap parolini (elektron pochtaga kirish) taqdim eting!
 - Elektron pochtada IMAP ruxsati yoqilgan bo'lishi kerak
 -  `SEMI_AUTOMATIC_APPROVE_LINK = False `  # Agar True boʻlsa, tasdiqlash havolasini elektron pochtadan CLIga qoʻlda joylashtirish imkonini beradi. Yuqoridagi barcha bayroqlar True ga o'rnatilishi kerak. Agar siz ushbu bayroqdan foydalansangiz, IMAP ruxsatini berishingiz shart emas
 -  `SINGLE_IMAP_ACCOUNT = False `  # agar sizda barcha tasdiqlangan xatlarni bitta IMAP manziliga yo'naltirish imkoniyati mavjud bo'lsa. Foydalanish: asosiy IMAP manzilingizdagi False ni "name@domain.com:password" ga o'zgartiring
 -  `EMAIL_FOLDER = "" `  # pochtaga tasdiqlash xati keladigan joyni avtomatik aniqlashi uchun o'tkazib yuboring, yoki pochta xat keladigan papkani yozing (Misol uchun "INBOX"
 -  `IMAP_DOMAIN = "" `  # avtomatik domen uchun o'tish, har doim ham ishlamaydi






### Konfiguratsiya 📧

1. Hisoblarni sozlash 🔒

   `data/accounts.txt` hisoblarini email:password (tdydjkhfuhhh@gmail.com:grass_parol123) formatida joylashtiring.


   
2. Proxy sozlash 🔒

   Proksi-serverlaringizni `data/proxies.txt` da *ANY* (socks, http/s, ...) formatida sozlang. (Misol uchun "http://login:parol@ip:port") 🌐



## Docker tomonidan tez boshlash
   1. Docker-CE ni o'rnating: `curl -sSL -k https://get.docker.com | sh`
   2. Docker Compose-ni o'rnating: `curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose`
   3. Manba kodini klonlash: `git clone https://github.com/JMSM0707/G-MAIN.git`
   4. Konfiguratsiya: O'zgartirish `data/accounts.txt` va `data/proxies.txt`
   5. Konteynerni ishga tushirish: `docker-compose up -d`

   PS: Qo'shimcha konfiguratsiyani ko'rish mumkin `docker-compose.yml`


## Foydalanuvchidan qo'shimcha qo'llanma 

### 1. Ma'lumotlar fayllarini sozlash

**accounts.txt** — Yozuvlar uchun format: `email:password:password`

Misol: `djfiudgddg@gmail.com:qwert123:qwert123`  
Birinchi parol Grass xizmatiga kirish uchun, ikkinchisi esa elektron pochta uchun.  
Agar sizda bir xil parolga ega elektron pochta xabarlari to'plami bo'lsa, bir xil paroldan ikki marta foydalaning.

**wallets.txt** — Solana shaxsiy kalitlarini Base58 formatida kiriting:

Ushbu havolada solana hamyon generatorni topishingiz mumkin: [Solana Wallet yarating](https://ct.app/createWallet/sol).

**proxies.txt** — Formada HTTP proksi-serverlaridan foydalaning `login:paarol@ip:port`.

---

### 2. Hisobni ro'yxatdan o'tkazish uchun konfiguratsiya

Yangi hisoblarni ro'yxatdan o'tkazish uchun quyidagi sozlamalardan foydalaning:

```plaintext
REGISTER_ACCOUNT_ONLY = True
MINING_MODE = False
```

**Ro'yxatdan o'tgan hisob ma'lumotlarini saqlash:**  
Muvaffaqiyatli ro'yxatdan o'tgan hisoblar bu yerda `\logs\new_accounts.txt` shu formatda: `email:password:nickname` saqlanadi.

Qo'shimcha natijalar fayllari:  
- `\logs\failed.txt` — muvaffaqiyatsiz ro'yxatga olish.  
- `\logs\success.txt` — muvaffaqiyatli ro'yxatdan o'tish.

---

### 3. Elektron pochtani tekshirish va hamyonga ulanishni sozlash

Elektron pochtani tekshirish va hamyonga ulanish uchun ushbu sozlamalardan foydalaning:

```plaintext
APPROVE_EMAIL = True
CONNECT_WALLET = True
SEND_WALLET_APPROVE_LINK_TO_EMAIL = True
APPROVE_WALLET_ON_EMAIL = True
----
REGISTER_ACCOUNT_ONLY = False
MINING_MODE = False
```

**Eslatma:** Ushbu sozlamalar elektron pochtaga hamyonni tasdiqlash havolasini yuboradi va ro'yxatdan o'tishni yakunlaydi.

---

### 4. Mining Mode

Mayning rejimini yoqish uchun quyidagi sozlamalardan foydalaning:

```plaintext
APPROVE_EMAIL = False
CONNECT_WALLET = False
SEND_WALLET_APPROVE_LINK_TO_EMAIL = False
APPROVE_WALLET_ON_EMAIL = False
----
REGISTER_ACCOUNT_ONLY = False
MINING_MODE = True
```

Shu bilan birga siz CONSOL yoki NODE rejimiga o'tishni tanlashingiz mumkin.
Buning uchun: `data/proxies.txt` dan sozlamalarni o'zgartirishingiz kerak.
Agar True bo'lsa - konsol versiyasidan foydalaniladi va interfeys ko'rinmaydi, agar False bo'lsa - konsol versiyasidan foydalanilmaydi va interfeys ko'rinadi
```ochiq matn
USE_CONSOLE_VERSION = True
NODE_TYPE = "2x"  # 1x, 1_25x, 2x

```
### 5. Captchani hal qilish

Hisob qaydnomalarini ro'yxatdan o'tkazish uchun captcha-ni hal qilish xizmati talab qilinadi.  
Mayning rejimida Captcha talab qilinmaydi.
