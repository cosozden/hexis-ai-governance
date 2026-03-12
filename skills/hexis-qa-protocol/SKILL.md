---
name: hexis-qa-protocol
description: >
  HEXIS marka kalite güvence protokolü. Tüm HEXIS çıktılarına (Cowork plugin, Claude Code projesi,
  LinkedIn içeriği, müşteri raporu, AIGP materyali, blog, sunum, web sayfası) 3 aşamalı testten geçirir.
  "test yap", "kontrol et", "doğrula", "yayına hazırla", "Faz 1/2/3", "kaynak doğrulama",
  "marka tutarlılığı", "QA", "audit", "review", "structural check", "source verification"
  gibi ifadeler geçtiğinde bu skill'i MUTLAKA kullan.
  Herhangi bir HEXIS çıktısı tamamlandığında kullanıcıya test öner.
  Yasal referans içeren çıktılarda Faz 2 ZORUNLU — Claude'un hafızasına güvenmek kabul edilemez,
  web_search kullanılmalı.
---

# HEXIS QA Protocol — 3 Phase Quality Assurance (v2)

## Temel Kural

**HEXIS markası kapsamında üretilen HER araç ve çıktı bu 3 aşamalı testten geçmelidir.**

Kapsam:
- Cowork plugin dosyaları (SKILL.md, commands, plugin.json, README, CHANGELOG)
- Claude Code projeleri (hexis-ai-governance repo dosyaları)
- LinkedIn içerikleri (carousel, infografik, text-only, video prompt)
- Müşteri çıktıları (raporlar, sunumlar, değerlendirmeler)
- AIGP çalışma materyalleri (practice sorular, terminoloji listeleri, Hexis içerikleri)
- Blog yazıları, web içerikleri, e-postalar
- Kod dosyaları (Python, JS, bash script vb.)

---

## FAZ 1 — FONKSİYONEL TEST

**Amaç:** Çıktı beklenen şekilde çalışıyor mu? İçerik doğru yapıda mı?

### Kontrol Listesi

**Genel (Tüm Çıktılar):**
- [ ] Çıktı kullanıcının talebine uygun mu?
- [ ] Dil tutarlılığı: User-facing = English (plugin) veya belirtilen dil
- [ ] Yazım/imla hataları yok mu?
- [ ] Format doğru mu? (md, json, pptx, docx vb.)

**Plugin / Kod Çıktıları:**
- [ ] ORIENT terminolojisi doğru mu? (Observe, Risk, Identify, Evaluate, Navigate, Track — "Risk-Assess" veya stage adı olarak "Implement/Evidence/Normalize" kullanılmamış)
- [ ] ORIENT 6 aşaması eksiksiz mi?
- [ ] Karar ağacı beklenen sınıflandırmayı üretiyor mu?
- [ ] EU AI Act risk kategorileri resmi terminolojiye uygun mu?
- [ ] JSON syntax geçerli mi? (plugin.json)
- [ ] Markdown rendering düzgün mü?
- [ ] Versiyon numaraları tüm dosyalarda tutarlı mı?

**LinkedIn İçerikleri:**
- [ ] Hook ilk 1-2 cümle geri kalanından 5x güçlü mü?
- [ ] ORIENT adımıyla etiketlenmiş mi?
- [ ] Hedef kitle için somut değer var mı?
- [ ] Jenerik AI hype'ından uzak, teknik gerçeğe dayalı mı?
- [ ] Claude Code görsel/video prompt'u eklenmiş mi?
- [ ] Hashtag'ler uygun mu?

**Kod Dosyaları (⚠️ RİSK KONTROLÜ):**
- [ ] rm, mv, chmod gibi yıkıcı komutlar wildcard olmadan mı yazılmış?
- [ ] Credential, API key, token düz metin olarak mı gömülmüş? (YASAK)
- [ ] Harici URL'ler güvenli mi? (https, bilinen kaynaklar)
- [ ] Infinite loop veya kaynak tüketen pattern var mı?
- [ ] pip install --break-system-packages gibi system-level risk var mı?

### Test Senaryoları (minimum 3)

Her fonksiyonel test en az 3 senaryo içermeli:
1. **Beklenen kullanım** — En yaygın use case
2. **Sınır durum** — Edge case
3. **Minimal/negatif** — En düşük risk veya geçersiz input

### Sonuç Formatı

```
╔══════════════════════════════════════════════════╗
   FAZ 1 — FONKSİYONEL TEST SONUÇ RAPORU
   Çıktı: [Çıktı adı ve versiyonu]
   Tarih: [YYYY-MM-DD]
╚══════════════════════════════════════════════════╝

SENARYO SONUÇLARI:
┌──────────────────────────┬────────┬───────────┐
│ Senaryo                  │ Sonuç  │ Kontrol   │
├──────────────────────────┼────────┼───────────┤
│ 1. [Senaryo adı]        │ ✅/❌  │ X/X       │
│ 2. [Senaryo adı]        │ ✅/❌  │ X/X       │
│ 3. [Senaryo adı]        │ ✅/❌  │ X/X       │
└──────────────────────────┴────────┴───────────┘

BULUNAN HATALAR: [sayı]
VERSİYON DEĞİŞİKLİĞİ GEREKLİ Mİ: Evet/Hayır

╔══════════════════════════════════════════════════╗
   FAZ 1 SONUÇ: ✅ PASS / ❌ FAIL
╚══════════════════════════════════════════════════╝
```

---

## FAZ 2 — KAYNAK DOĞRULAMA

**Amaç:** Tüm yasal/düzenleyici referanslar harici kaynaklardan doğrulanmış mı?

### KRİTİK KURAL

> **Claude'un hafızasına güvenmek YASAKTIR.**
> Her yasal referans (article numarası, tarih, ceza miktarı, tanım) web_search ile harici kaynaktan doğrulanmalıdır.

> **BİRİNCİL KAYNAK ZORUNLULUĞU:** Ceza rakamları, tarihler, madde numaraları ve territorial scope için ikincil kaynak (hukuk firması blogu, compliance sitesi) ASLA yeterli değildir. Resmi metin doğrudan web_fetch ile okunmalıdır. İkincil kaynaklarda konsensüs olsa bile bu kural geçerlidir — v0.2.1 QA'da 30M€/%6 hatası bu nedenle oluştu.

**Zorunlu birincil URL'ler:**
- Yaptırım rakamları → artificialintelligenceact.eu/article/99/
- Uygulama takvimi → artificialintelligenceact.eu/article/113/
- Territorial scope → artificialintelligenceact.eu/article/2/
- Yüksek riskli liste → artificialintelligenceact.eu/annex/3/

### KAPSAM İFADESİ TETİKLEYİCİSİ ⚠️

**Bu kural, article numarası veya ceza miktarı olmasa bile geçerlidir.**

"zorunlu", "tabi", "gerektiriyor", "kapsamında", "yükümlü", "subject to", "required to", "must comply" gibi kelimeler içeren HER cümle Faz 2'yi tetikler. Kapsam iddiası içerik tamamlanmadan önce primary source ile doğrulanır — deployment sonrası değil.

**EU AI Act Kapsam — Kalıcı Yasak Liste:**

| ❌ YASAK İFADE | ✅ DOĞRU ÇERÇEVE |
|---|---|
| "Türkiye'de AI kullanan her şirket EU AI Act'e tabi" | "AB pazarına açık veya AB'deki kullanıcılara hizmet veren Türk şirketler" |
| "Türk işletmeleri EU AI Act kapsamında" | "AB pazarında faaliyet gösteren Türk şirketler için EU AI Act yükümlülüğü doğar" |
| "Turkish organisations subject to the EU AI Act" | "Turkish organisations operating in or serving the EU market" |
| "Türkiye'de yapay zeka sistemi çalıştırmak EU AI Act'i gerektirir" | "AB pazarına yönelik AI sistemleri için EU AI Act uyum yükümlülüğü doğar" |

**Hukuki dayanak:** EU AI Act Art. 2(1)(a)(c) — kapsam üçüncü ülke operatörleri için AB'ye sunum VEYA çıktının AB'de kullanımı koşuluna bağlıdır.

### Doğrulanacak Referans Tipleri

| Tip | Örnek | Doğrulama Kaynağı |
|-----|-------|-------------------|
| EU AI Act article | Art. 5(1)(h) | artificialintelligenceact.eu, EUR-Lex |
| Annex referansı | Annex III Area 4(a) | artificialintelligenceact.eu/annex/ |
| Ceza miktarı | €35M / 7% | euaiact.com/article/99 |
| Yürürlük tarihi | Feb 2025 | Art. 113, hukuk firması analizleri |
| ISO standardı | ISO/IEC 42001:2023 §6.1.2 | iso.org |
| KVKK maddesi | 6698 sayılı Kanun Md. 5 | kvkk.gov.tr |
| NIST AI RMF | GOVERN function | nist.gov |
| OECD AI Principles | Principle 1.2 | oecd.ai |
| Digital Omnibus | Proposed Nov 2025 | EUR-Lex, IAPP, law firm analyses |
| AIGP BoK | Domain II.C | iapp.org |

### Doğrulama Süreci

1. Çıktıdaki tüm yasal/düzenleyici referansları listele
2. Her biri için web_search yap (minimum 2 farklı kaynak)
3. Orijinal metin ile çıktıdaki ifadeyi karşılaştır
4. Uyuşmazlık varsa NOT olarak işaretle
5. Sonuç tablosunu doldur

### Sonuç Formatı

```
╔══════════════════════════════════════════════════╗
   FAZ 2 — KAYNAK DOĞRULAMA RAPORU
   Çıktı: [Çıktı adı ve versiyonu]
   Tarih: [YYYY-MM-DD]
╚══════════════════════════════════════════════════╝

| # | Referans | Çıktıdaki İfade | Doğrulama Kaynağı | Sonuç |
|---|---------|-----------------|-------------------|-------|
| 1 | [Ref]   | [İfade]         | [Kaynak URL/adı]  | ✅/❌ |

Kritik hata: [sayı]
Minor iyileştirme: [sayı]

╔══════════════════════════════════════════════════╗
   FAZ 2 SONUÇ: ✅ PASS / ❌ FAIL
╚══════════════════════════════════════════════════╝
```

---

## FAZ 3 — YAPISAL BÜTÜNLÜK

**Amaç:** Çıktı HEXIS marka standartlarına ve proje yapısına uygun mu?

### Kontrol Listesi

**HEXIS Marka Tutarlılığı:**
- [ ] Marka sesi: Açık, otoriter, pratik, hype'tan uzak mı?
- [ ] "Compliance as orientation, not checklist" felsefesine uygun mu?
- [ ] ORIENT framework doğru referans verilmiş mi?
- [ ] hexis.center URL doğru mu?
- [ ] Görsel standartlar: koyu lacivert #0A1628, akik mavi #2D6BE4, amber #F59E0B

**Türkçe İçerik — Em Dash Yasağı ⚠️:**
- [ ] Türkçe metinde `—` (em dash) veya cümle içi `-` (tire) kullanılmamış mı?
- Yasak: `"Örtüşen gereksinimler — ve yönetilmesi gereken gerilim noktaları."`
- Alternatifler: virgül (ek bilgi/liste), noktalı virgül (bağlantılı düşünceler), iki nokta (açıklama/liste), parantez (yan bilgi/teknik terim)
- Bu kural HTML içerikler, LinkedIn gönderileri, blog yazıları ve tüm Türkçe çıktılar için geçerlidir.
- **İngilizce içeriklerde em dash serbesttir.**

**Dosya/Proje Yapısı:**
- [ ] Dosya adlandırma uygun mu?
- [ ] Versiyon numaraları senkron mu? (plugin.json ↔ CHANGELOG ↔ README ↔ SKILL.md)
- [ ] CHANGELOG güncel mi?
- [ ] README değişiklikleri yansıtıyor mu?
- [ ] Git commit mesajı açıklayıcı mı?

**Çapraz Referans Kontrolü:**
- [ ] Bir dosya değişince referans veren TÜM dosyalar güncellenmiş mi?
- [ ] Terminoloji tüm dosyalarda tutarlı mı?
- [ ] Eski terminoloji hiçbir yerde kalmamış mı?

### Sonuç Formatı

```
╔══════════════════════════════════════════════════╗
   FAZ 3 — YAPISAL BÜTÜNLÜK RAPORU
   Çıktı: [Çıktı adı ve versiyonu]
   Tarih: [YYYY-MM-DD]
╚══════════════════════════════════════════════════╝

MARKA TUTARLILIĞI: ✅/❌
DOSYA YAPISI: ✅/❌
ÇAPRAZ REFERANS: ✅/❌
ERİŞİLEBİLİRLİK: ✅/❌

╔══════════════════════════════════════════════════╗
   FAZ 3 SONUÇ: ✅ PASS / ❌ FAIL
╚══════════════════════════════════════════════════╝
```

---

## GENEL QA SONUÇ RAPORU

```
╔══════════════════════════════════════════════════════════════╗
   HEXIS QA PROTOCOL — GENEL SONUÇ
   Çıktı: [Ad ve versiyon]  |  Tarih: [YYYY-MM-DD]
╠══════════════════════════════════════════════════════════════╣
│  Faz 1 — Fonksiyonel Test:      ✅ PASS / ❌ FAIL         │
│  Faz 2 — Kaynak Doğrulama:      ✅ PASS / ❌ FAIL         │
│  Faz 3 — Yapısal Bütünlük:      ✅ PASS / ❌ FAIL         │
╠══════════════════════════════════════════════════════════════╣
│  GENEL SONUÇ: ✅ YAYIN HAZIR / ❌ DÜZELTME GEREKLİ        │
│  Kritik hata: [sayı]  |  Minor: [sayı]                      │
│  Versiyon değişikliği: Evet/Hayır                            │
╚══════════════════════════════════════════════════════════════╝
```

---

## KOD RİSK DEĞERLENDİRME PROTOKOLÜ

**Tetikleyici:** Claude bir kod dosyası yazdığında veya düzenlediğinde otomatik.

| Seviye | Tanım | Eylem |
|--------|-------|-------|
| 🟢 DÜŞÜK | Okuma, gösterim, hesaplama | Normal devam |
| 🟡 ORTA | Dosya oluşturma, pip install, network | Kullanıcıya bilgi ver |
| 🔴 YÜKSEK | rm, chmod, git push --force, credential | DURDUR + onay iste |
| ⛔ KRİTİK | Wildcard silme, system dosyası, API key açık metin | YASAK — alternatif öner |

---

## ORIENT Framework Referansı (v0.2.1)

| Harf | Aşama | Eski Adı (KULLANMA) | Açıklama |
|------|-------|---------------------|----------|
| **O** | Observe | — | AI sistemini, bağlamını ve etkilenen kişileri haritalandır |
| **R** | Risk | ~~Risk-Assess~~ | EU AI Act'a göre risk sınıflandırması yap |
| **I** | Identify | ~~Implement~~ | Uygulanabilir yasal yükümlülükleri belirle |
| **E** | Evaluate | ~~Evidence~~ | Mevcut kontrolleri ve uyum düzeyini değerlendir |
| **N** | Navigate | — | Organizasyonun olgunluk ve kaynaklarına göre önceliklendirilmiş aksiyon haritası çiz |
| **T** | Track | — | Sürekli izleme, review tetikleyicileri ve iyileştirme döngüsü |

**Yasak kombinasyonlar:** "Risk-Assess", "Implement" veya "Evidence" asla ORIENT aşama adı olarak kullanılmaz. "Normalize" hiçbir zaman bir ORIENT aşama adı olmadı — eski tartışmalarda geçiyorsa ignore et.

---

## Kullanım Kalıpları

| Kullanıcı der ki | Ne yapılır |
|---|---|
| "test yap" / "QA" | 3 faz sırasıyla uygula |
| "Faz 1" / "fonksiyonel test" | Sadece Faz 1 |
| "Faz 2" / "kaynak doğrula" | Sadece Faz 2 (web search zorunlu) |
| "Faz 3" / "yapısal kontrol" | Sadece Faz 3 |
| "yayına hazırla" | 3 faz + genel rapor |
| "bu kodu kontrol et" | Kod risk değerlendirme protokolü |
| "hızlı kontrol" | Sadece Faz 1 (hızlı) |
| [Çıktı tamamlandığında] | "QA testi yapayım mı?" öner |
