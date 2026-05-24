# Yunanistan Golden Visa Landing Page · Avla Real Estate

Canlı URL: https://www.avlarealestate.com/yunanistan-golden-visa
Wix Site ID: `a211dbfc-9c5e-44ec-aeff-64a7a120dffd` (Avla Gayrimenkul A.Ş)

## Klasör yapısı

```
yunanistan-golden-visa/
├── index.html              ← TEK BİRLEŞİK SAYFA (3 bölüm + sticky + pop-up + tracking)
├── README.md               ← bu dosya
├── sections/               ← Wix'te 3 ayrı HTML embed olarak kullanılan parçalar
│   ├── 01_ust.html         ← Hero + HubSpot form + "Nedir?" + "Neden Avla?"
│   ├── 02_orta.html        ← Detaylı raporlar + portföy kartları
│   └── 03_alt.html         ← Süreç + hukuk + SSS + final CTA
└── _originals/             ← Wix CDN'den çekilmiş orijinal yedekler (canlı versiyon)
    ├── 01_ust_original.html
    ├── 02_orta_original.html
    └── 03_alt_original.html
```

## Mevcut canlı yapı

Wix sayfa şu an **3 ayrı HTML Embed widget** olarak çalışıyor:

| Widget | iframe src (canlı) |
|---|---|
| Üst | `filesusr.com/html/0503e3_f2f9...8a2d.html` |
| Orta | `filesusr.com/html/0503e3_0a1c...e618.html` |
| Alt | `filesusr.com/html/0503e3_5755...c909.html` |

## Yeni içerikte değişen şeyler

### `sections/01_ust.html` (Üst — değiştirildi)
- **HubSpot form embed eklendi** (`portal 145141452` / form `6602f22f-ef64-4465-a564-5f698bf7918d`)
- Mavi karttaki "Forma Git" butonu kaldırıldı (form artık zaten görünür)
- Tüm CTA'lara `data-cta="..."` etiketi → GTM tracking için
- Anchor link `#form` ile sayfa içi scroll

### `sections/02_orta.html` (Orta — kopya)
- Şu anki canlı sürümle aynı
- CTA'lara `data-cta` etiketi eklendi (tracking için)

### `sections/03_alt.html` (Alt — kopya)
- Şu anki canlı sürümle aynı
- `Forma Git ↑` butonu artık `#form` anchor'a gidiyor

### `index.html` (Birleşik tek sayfa — YENİ)
3 bölümü tek HTML'de birleştirip eklenenler:
- **GTM placeholder** — `GTM-XXXXXXX`'i kendi container ID'nizle değiştirin
- **HubSpot form embed** (hero'da inline)
- **Sticky mobil CTA bar** (alt 64px: 📞 Ara + 💬 WhatsApp)
- **Akıllı pop-up CTA** — exit-intent (desktop) veya scroll %60+25s (mobile). localStorage cookie ile 7 günde 1 kez açılır
- **Click tracking** — `data-cta` etiketli her butona `phone_click` / `whatsapp_click` / `cta_click` event'i dataLayer'a push
- **Anchor navigation** — `#form` (hero) ve `#sss` (SSS bölümü)
- **SEO meta** — title, description, Open Graph

## Wix'e nasıl yapıştırılır?

### Seçenek A — Mevcut 3 widget'ı güncelle (önerilen, en az risk)
1. Wix Editor'da sayfayı aç
2. **Üst** widget'a tıkla → "Edit Code" → mevcut HTML'i sil → `sections/01_ust.html` içeriğini yapıştır
3. **Orta** widget için aynı işlemi `sections/02_orta.html` ile yap
4. **Alt** widget için aynı işlemi `sections/03_alt.html` ile yap
5. "Save & Publish"
6. Pop-up CTA ve sticky bar için: 4. bir widget eklenir veya **header/footer custom code**'a JS olarak konur

> ⚠️ **Önemli:** Wix HTML Embed widget'ı sandbox'lı iframe olarak çalışır. `position:fixed` widget'ın **iframe içinde** çalışır — sayfanın tamamında değil. Yani sticky bar + pop-up için **Wix Settings → Custom Code** kullanmak daha doğru (aşağı bak).

### Seçenek B — Tek widget olarak çalıştır (deneysel)
1. Wix Editor'da sayfanın mevcut 3 widget'ını sil
2. Tek bir büyük HTML Embed widget ekle, **yüksekliği "Full page" yap** (Wix izin verirse)
3. `index.html` içeriğini yapıştır
4. Pop-up + sticky CTA'lar widget içinde çalışır ama parent sayfanın navigasyonu da iframe içine sıkışır

### Seçenek C — Sticky CTA + pop-up'ı site-wide kur (en doğru yol)
1. Wix Editor → **Settings → Custom Code → Head**'e:
   ```html
   <!-- HubSpot embed (zaten yapıştırılacak) -->
   <script src="https://js-eu1.hsforms.net/forms/embed/145141452.js" defer></script>
   <!-- GTM container -->
   ```
2. **Body End**'e: `index.html`'in `<script>` bloğunu (pop-up + tracking) yapıştır
3. Sticky CTA'yı **Body End**'e CSS+HTML olarak ekle
4. Mevcut 3 widget olduğu gibi kalır, sticky/pop-up site-wide çalışır

## GTM kurulumu (kritik — şu an sıfır tracking var)

`index.html` `GTM-XXXXXXX` placeholder'ı içeriyor. Yapılması gerekenler:

1. **GTM Container oluştur** (varsa ID'sini öğren)
2. `GTM-XXXXXXX` (3 yerde — `<script>`, `<noscript>`) → container ID ile değiştir
3. GTM içinde:
   - **Trigger**: Custom Event `phone_click`, `whatsapp_click`, `cta_click`, `popup_open`
   - **Tag**: GA4 Event (event_name = `{{Event}}`, parameters = `cta_label`, `page_project`)
   - **Tag**: Google Ads Conversion (her custom event için bir conversion action)
4. GA4 hesabını kur (varsa Measurement ID'sini al)
5. Google Ads'te dönüşüm import'u yap (GA4 → "Birincil dönüşüm")

## Eksikler (sonraki adımlarda)

- [ ] €800K yasası güncellemesi (yeni Yunan yasası — sayfada eksik)
- [ ] Testimonial / başarı hikayeleri
- [ ] Yunanistan vs Portekiz vs İspanya karşılaştırma tablosu
- [ ] İngilizce versiyon
- [ ] Yeni proje görselleri (Hera, Kareas, Boulevard vs.)
- [ ] Open Graph image (1200x630)
