# Wix SEO Panel — 5 Dakikada Tamamla

> **Yol:** Wix Editor → Yunanistan Golden Visa sayfası → "..." → **Page Settings** (veya sayfa ismi üzerinde sağ tık → SEO)

---

## ADIM 1 — Social share sekmesi (en kritik)

**Yol:** Page Settings → **Social share**

### 1.1 Social image
- **"+ Upload image"** → dosya seç:
  `/Users/sami/Library/CloudStorage/GoogleDrive-saka1966@gmail.com/My Drive/EMLAK/ATİNA/Landing Pages/yunanistan-golden-visa/wix-deploy/og-cover.png`
- 1200×630, 255 KB

### 1.2 Social share title
```
Yunanistan Golden Visa · Akılcı bir AB yatırımı
```

### 1.3 Social share description
```
Türk kahvenizi yudumlayın, biz size Atina yolunu çıkaralım. €250.000 ile AB oturumu, 4-6 ay tipik süreç. 30 saniyede ücretsiz yol haritası.
```

---

## ADIM 2 — SEO basics sekmesi (Google için)

### 2.1 Page title (SEO)
```
Yunanistan Golden Visa 2026 · €250K AB Oturumu Yatırımı | Avla
```

### 2.2 Page description (meta)
```
Yunanistan Golden Visa programıyla €250.000 yatırım karşılığında AB oturumu. 4-6 ay tipik süreç, tüm aile dahil, Schengen seyahat hakkı. Türk yatırımcılara özel ücretsiz danışmanlık — 30 saniyede yol haritası.
```

### 2.3 URL slug
```
yunanistan-golden-visa
```
(zaten doğru, dokunma)

### 2.4 Index this page
☑ **AÇIK** (Google indexlesin)

---

## ADIM 3 — Advanced SEO → Additional tags (9 tag)

**Yol:** Advanced SEO → Additional tags → **+ Add New Tag** (9 kez)

| Tip | name / property | content |
|---|---|---|
| meta property | `og:image:width` | `1200` |
| meta property | `og:image:height` | `630` |
| meta property | `og:image:type` | `image/png` |
| meta property | `og:image:alt` | `Yunanistan Golden Visa — Avla Real Estate` |
| meta property | `og:locale` | `tr_TR` |
| meta name | `twitter:card` | `summary_large_image` |
| meta name | `twitter:title` | `Yunanistan Golden Visa · Akılcı bir AB yatırımı` |
| meta name | `twitter:description` | `Türk kahvenizi yudumlayın, biz size Atina yolunu çıkaralım ☕` |
| meta name | `twitter:image` | (Adım 1.1'de yüklediğin görselin Wix CDN URL'si — Social share kaydedince Wix sana verir, ordan kopyala) |

> **Not:** Wix Additional Tags arayüzü genelde "name + content" çiftiyle çalışır. `og:` ile başlayanlar **property** olarak ekleniyor, `twitter:` ile başlayanlar **name** olarak. Wix bazı versiyonlarda otomatik tip seçer; sen sadece **name** alanına `og:image:width` gibi yazar, **content** alanına `1200` koyarsın.

---

## ADIM 4 — Structured data markup (2 JSON-LD)

**Yol:** Advanced SEO → Structured data markup → **+ Add New Markup**

### 4.1 Markup adı: `Service` (RealEstateAgent + Golden Visa hizmeti)

JSON içeriği (olduğu gibi yapıştır):

```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Yunanistan Golden Visa Danışmanlık",
  "serviceType": "Golden Visa Investment Consulting",
  "provider": {
    "@type": "RealEstateAgent",
    "name": "Avla Gayrimenkul A.Ş.",
    "url": "https://www.avlarealestate.com",
    "telephone": "+90-532-282-26-57",
    "email": "realestate@avla.com.tr",
    "address": {
      "@type": "PostalAddress",
      "addressLocality": "İstanbul",
      "addressCountry": "TR"
    },
    "sameAs": [
      "https://www.avlarealestate.com",
      "https://south.moschato.avlarealestate.com"
    ]
  },
  "areaServed": {
    "@type": "Country",
    "name": "Greece"
  },
  "audience": {
    "@type": "Audience",
    "geographicArea": {
      "@type": "Country",
      "name": "Turkey"
    }
  },
  "description": "Yunanistan Golden Visa programı için Türk yatırımcılara özel ücretsiz danışmanlık. €250.000 yatırımla AB oturumu, 4-6 ay tipik süreç, 24 saat içinde uzman dönüşü.",
  "offers": {
    "@type": "Offer",
    "price": "250000",
    "priceCurrency": "EUR",
    "description": "Minimum yatırım — €250.000",
    "availability": "https://schema.org/InStock"
  },
  "potentialAction": {
    "@type": "ContactAction",
    "target": "https://www.avlarealestate.com/yunanistan-golden-visa#Form",
    "name": "Ücretsiz Yol Haritası İste"
  }
}
```

### 4.2 Markup adı: `FAQPage` (Google rich snippet için)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Yunanistan Golden Visa için minimum yatırım nedir?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Atina ve diğer büyük şehir bölgelerinde €250.000'dan başlar. Lokasyona göre eşikler değişebilir."
      }
    },
    {
      "@type": "Question",
      "name": "Süreç ne kadar sürer?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Tipik olarak 4-6 ay arasında tamamlanır. Belge hazırlığı, mülk seçimi ve biyometrik randevu adımlarını kapsar."
      }
    },
    {
      "@type": "Question",
      "name": "Tüm aile dahil mi?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Evet — eş, 21 yaşına kadar çocuklar ve bakmakla yükümlü olunan ebeveynler dahil edilebilir."
      }
    },
    {
      "@type": "Question",
      "name": "Schengen seyahat hakkı veriyor mu?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Evet. Golden Visa sahibi olarak 90/180 gün kuralı çerçevesinde Schengen bölgesinde serbestçe seyahat edebilirsiniz."
      }
    },
    {
      "@type": "Question",
      "name": "Yunan vatandaşlığına ne zaman başvurabilirim?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "7 yıl yasal ikamet sonrası vatandaşlık başvurusu yapılabilir. Yatırım bu süreyi otomatik kısaltmaz; ikamet şartı geçerli."
      }
    }
  ]
}
```

---

## ADIM 5 — Robots meta tag

Senin ekranda gördüğüm checkbox'lar:
- ❌ noindex
- ❌ nofollow
- ❌ nosnippet
- ❌ noarchive
- ❌ noimageindex
- ❌ max-image-preview
- ❌ max-snippet
- ❌ max-video-preview

**HEPSİ BOŞ KALSIN.** Şu an doğru, dokunma.

---

## ADIM 6 — Save & Publish

1. Page Settings panelinde **Save** → kapat
2. Editor üst sağda **Publish** → canlı al

---

## ADIM 7 — Test (Publish sonrası 2 dakika sonra)

### 7.1 Open Graph önizleme
- https://www.opengraph.xyz/url/https%3A%2F%2Fwww.avlarealestate.com%2Fyunanistan-golden-visa
- Görseli, başlığı, açıklamayı kontrol et — Facebook/WhatsApp/LinkedIn'de böyle görünecek.

### 7.2 Twitter Card önizleme
- https://cards-dev.twitter.com/validator
- URL'yi gir: `https://www.avlarealestate.com/yunanistan-golden-visa`

### 7.3 Google Rich Results
- https://search.google.com/test/rich-results
- URL'yi gir → Schema'lar "Valid" olmalı (Service + FAQPage).

### 7.4 Facebook Sharing Debugger
- https://developers.facebook.com/tools/debug/
- URL gir → **Scrape Again** → görsel + metin önizlemesi.

### 7.5 WhatsApp test
- Sayfa URL'sini herhangi bir WhatsApp sohbetine yapıştır
- 1-2 saniye sonra OG cover + başlık önizlemesi çıkmalı

---

## Neden API ile yapamadık?

Wix REST API spec'inde per-page SEO/Social share/Structured data **yazma endpoint'i yok**. Sadece okuma var (`resolve-static-page-seo-tags`). Bu paneli sadece Editor UI'dan dolduruyoruz.

İyi yan: bir kere doldur → tüm kanallarda (Google, FB, WA, LinkedIn, Twitter) tutarlı önizleme + rich snippet.

---

## Sıradaki adımlar (publish sonrası)

1. **Google Search Console**: avlarealestate.com property → yeni sayfa için "Inspect URL" → "Request indexing"
2. **GTM**: HTML'deki `GTM-XXXXXXX` placeholder'ı kendi container ID'nle değiştir (3 yer)
3. **Google Ads**: RSA reklam metinlerini telefon ağırlıklı yenile (#19 task pending)
