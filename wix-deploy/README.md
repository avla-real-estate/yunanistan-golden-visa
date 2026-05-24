# Wix'e Yapıştırma Talimatı

## 📦 Dosya
`yunanistan-golden-visa.html` — **617 KB** tek dosya (logo dahil)

Hiçbir dış görsel/asset referansı yok. Logo PNG base64 olarak HTML içine gömüldü. Tek dosyayı kopyala-yapıştır yeterli.

## 🚀 Wix'e Yapıştırma Adımları

1. **Wix Editor'a giriş**: avlarealestate.com → Edit Site → "Yunanistan Golden Visa" sayfası
2. **Mevcut 3 HTML Embed widget'ını seç ve sil** (Üst / Orta / Alt)
3. Yerine **tek bir HTML Embed widget** ekle:
   - Add (+) → Embed Code → **HTML iframe**
4. Widget'a tıkla → **Enter Code** veya **Edit Code** butonuna bas
5. `yunanistan-golden-visa.html` dosyasını text editor'de aç (veya Mac'te `Cmd+A` ile kopyala)
6. **Tüm içeriği** Wix code editor'üne yapıştır
7. **Save** ya da **Update**
8. Widget'ı sürükle, sayfanın tamamını kaplayacak şekilde **yükseklik ayarla**:
   - Tipik: **3500–4500px** (içerik full görünmeli)
   - Test ile bul → scroll ettiğinde son section (footer) iframe içinde görünmeli
9. **Publish**

## ⚙️ GTM (Tracking) Aktivasyonu — Sonra

HTML'de placeholder `GTM-XXXXXXX` var (3 yerde, yorum içinde). Aktif olması için:

1. Wix sayfasında `Ctrl+F` ile `GTM-XXXXXXX` ara
2. Tüm 3 yerde kendi container ID'nle değiştir (ör. `GTM-K1A2B3C`)
3. JS bloğundaki yorum işareti `//` `(function(w,d,s,l,i)...` satırından kaldır
4. Save

> 🎯 GTM aktif olunca: `phone_click`, `whatsapp_click`, `form_submit`, `popup_open` event'leri otomatik akar.

## 🧪 Test Sonrası Kontrol

Wix'e yapıştırdıktan sonra:
- ✅ Hero formu doldur → `Ücretsiz Yol Haritası İste` → HubSpot'a düşmeli (form GUID `6602f22f-ef64-4465-a564-5f698bf7918d` zaten kayıtlı)
- ✅ Mobil görünüm: sticky CTA bar altta görünür mü?
- ✅ "Diğer Avla Projeleri" kartlarındaki görseller yüklenir mi? (south.moschato.avlarealestate.com'dan gelir)
- ✅ Pop-up: 25 saniye + scroll %60 sonrası açılır mı?

## ⚠️ Wix Iframe Bilinen Davranışlar

| Konu | Davranış |
|---|---|
| `position:fixed` (sticky CTA, FAB, popup) | Iframe **viewport'una göre** sabitlenir. Parent Wix sayfası scroll yapınca iframe içeriği görsel olarak kayar. Sticky bar iframe içinde sabit ama parent scroll'da hareketli görünür. |
| Form submit | `fetch` HubSpot API'ye gider. CORS açık, sorunsuz. |
| `localStorage` (pop-up cookie) | Çalışır (try/catch korumalı, sorun olursa sessizce skip). |
| External linkler | `target="_blank"` ile yeni sekme açar. |
| Anchor scroll (`#form`, `#sss`) | Iframe içinde smooth scroll. |

## 🔄 Logo Güncelleme

Logo dosyası değişirse:
1. Yeni PNG'i `assets/logos/avla-kus-tight.png` olarak kaydet
2. Aşağıdaki komutu çalıştır (proje kök dizininde):
```bash
B64=$(base64 -i assets/logos/avla-kus-tight.png | tr -d '\n')
python3 -c "
import sys
with open('index.html','r') as f: html=f.read()
html=html.replace('assets/logos/avla-kus-tight.png', f'data:image/png;base64,{open(\"/dev/stdin\").read()}')
with open('wix-deploy/yunanistan-golden-visa.html','w') as f: f.write(html)
" <<< "$B64"
```

## 📊 HubSpot Form GUID

- **Form**: "Yunanistan Golden Visa - Hızlı Lead Formu (Web)"
- **Internal GUID**: `6602f22f-ef64-4465-a564-5f698bf7918d`
- **Share URL**: `https://2eevv0.share-eu1.hsforms.com/2ZgLyL-9kRGWlZF9pi_eRjQ`
- **Portal ID**: `145141452`
- **Submission endpoint**: `https://api.hsforms.com/submissions/v3/integration/submit/145141452/6602f22f-ef64-4465-a564-5f698bf7918d`

## 📋 Field Eşleşmeleri

| Form Alanı | HubSpot Property | Type |
|---|---|---|
| Ad | `firstname` | text |
| Soyad | `lastname` | text |
| E-posta | `email` | email |
| Telefon | `phone` | tel |
| Yatırım Bütçesi | `gv_yatrm_butcesi_web` | enum |
| Yatırıma Hazırlık | `gv_yatrm_zamanlamas_web` | enum |
| KVKK Onayı | `gv_kvkk_onay_web` | `"true"` |
