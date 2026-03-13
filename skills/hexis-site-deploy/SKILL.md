---
name: hexis-site-deploy
description: >
  hexis.center reposuna yapılan her değişiklik için standart deploy iş akışı.
  "deploy et", "yayınla", "push et", "commit at", "siteye gönder", "canlıya al",
  "değişiklikleri kaydet" gibi ifadeler geçtiğinde MUTLAKA kullan.
  QA geçmeden deploy yapılmaz — bu kural devre dışı bırakılamaz.
---

# hexis-site-deploy — Standart Deploy İş Akışı

## Kural

Deploy = QA + commit + push. Bu üçü birbirinden ayrılamaz. QA'dan geçmeyen hiçbir değişiklik canlıya gitmez.

---

## Adım 1 — Değişen Dosyaları Tespit Et

```bash
git diff --name-only
git status
```

Değişen her HTML/JS/CSS dosyası için aşağıdaki QA adımlarını uygula.

---

## Adım 2 — QA Faz 1: Terminoloji ve İçerik Kontrolü

```bash
# ORIENT terminoloji — yasak terimler (0 satır = PASS)
grep -n "Risk-Assess\|Normalize\|Implement\|Evidence" [dosya.html]

# Türkçe içerik — em dash yasağı (0 satır = PASS)
# Not: İngilizce içeriklerde em dash serbesttir
grep -n " — \| - " [dosya.html]

# Art. 99(3) qualifier — ceza referansı varsa kontrol et
grep -n "99(3)\|penalty\|ceza" [dosya.html]
# Varsa "whichever is higher" ibaresini doğrula
```

| Sonuç | Eylem |
|-------|-------|
| 0 satır | ✅ PASS |
| Herhangi bir satır | ❌ FAIL → düzelt, tekrar tara |

---

## Adım 3 — QA Faz 2: Yasal Referans Doğrulaması

**Değişen içerikte yasal/düzenleyici referans varsa zorunlu. Yoksa ⏭ SKIP.**

`web_search` ile birincil kaynaktan doğrula:

| Referans tipi | Birincil kaynak |
|---------------|----------------|
| EU AI Act madde/tarih/ceza | eur-lex.europa.eu veya artificialintelligenceact.eu |
| KVKK maddesi | kvkk.gov.tr |
| ISO 42001 | iso.org |
| NIST AI RMF | nist.gov |
| Digital Omnibus | EUR-Lex, IAPP |

Doğrulanamayan iddialar için ifadeyi yumuşat: "...olarak değerlendirilmektedir" — kaynaksız kesin ifade kullanma.

---

## Adım 4 — QA Faz 3: Yapısal Bütünlük

```bash
# CSS token kontrolü — var() yapıları korunmuş mu?
grep -c "var(--" [dosya.html]
# Sayı commit öncesiyle aynı olmalı

# HTML syntax kontrolü
python3 -c "
from html.parser import HTMLParser
class Check(HTMLParser): pass
with open('[dosya.html]') as f:
    Check().feed(f.read())
print('HTML OK')
"

# generator/index.html için ek: cross-scope bridge
grep -n "window._obsLang" generator/index.html
# Mevcut olmalı
```

Kontrol listesi:
- [ ] CSS `var(--token)` yapıları bozulmamış
- [ ] HTML syntax hatası yok
- [ ] JavaScript IIFE yapıları korunmuş
- [ ] `window._obsLang` bridge mevcut (generator değiştiyse)

---

## QA Özet Raporu

Her deploy öncesi bu raporu üret:

```
QA RAPORU
──────────────────────────────────────
Faz 1 — Terminoloji/İçerik:  ✅ PASS / ❌ FAIL
Faz 2 — Yasal Doğrulama:     ✅ PASS / ❌ FAIL / ⏭ SKIP
Faz 3 — Yapısal Bütünlük:    ✅ PASS / ❌ FAIL
──────────────────────────────────────
GENEL: ✅ DEPLOY HAZIR / ❌ DEPLOY DURDURULDU
```

**Herhangi bir FAIL → deploy yapma. Düzelt, tekrar tara.**

---

## Adım 5 — Commit Hazırlığı

```bash
# Konumu doğrula
pwd
# Beklenen: hexis.center repo dizini

# Stage et — tek tek, gözden geçirerek
git add [değişen dosyalar]
# ASLA: git add . veya git add -A
```

**Commit mesajı formatı:**
```
[araç/sayfa]: [ne değişti] ([kapsam])
```

Örnekler:
```
generator: add Digital Omnibus uncertainty note (Annex III display)
checklist: fix ORIENT stage label — Identify not Implement
blog: add inference risk article (TR)
fria: update Art. 27 reference
tools: blog-converter.py güncellendi
docs: CLAUDE.md session protocol eklendi
```

Kurallar:
- Tek satır, max 72 karakter
- Türkçe kabul edilir
- Birden fazla araç değiştiyse virgülle listele veya ayrı commit

---

## Adım 6 — Push ve Deploy

```bash
git commit -m "[commit mesajı]"
git push origin main
```

**Yasak:**
- `git push --force` — izin istenmeden yapılmaz
- Toplu dosya silme — tek tek, onay alınarak

Cloudflare Pages push sonrası otomatik deploy başlatır (1-2 dakika).

---

## Adım 7 — Deploy Doğrulama

1. Değişen sayfayı tarayıcıda aç
2. Hard refresh: `Cmd+Shift+R` (Mac) / `Ctrl+Shift+R` (Win)
3. Değişiklik görünüyor mu? ✅ PASS
4. Görünmüyor mu? → Cloudflare dashboard → Caching → Purge Everything

---

## Adım 8 — Oturum Sonu Kayıt

Deploy tamamlandıktan sonra chat'te bildir:

```
Deploy tamamlandı.
Değişen dosyalar: [liste]
Commit: [mesaj]
QA: ✅ PASS
Canlı: hexis.center/[sayfa]
```

Ardından "Oturumu kapat" ile hafızayı güncelle.

---

## Hızlı Referans — hexis.center Dosya Yapısı

| Dosya | İçerik | ORIENT Aşaması |
|-------|--------|----------------|
| `generator/index.html` | Observe form + Risk Classifier + Governance Matrix | Observe → Risk |
| `checklist/index.html` | EU AI Act compliance checklist | Identify → Evaluate |
| `fria/index.html` | FRIA şablonu | Evaluate |
| `eu-ai-act-checklist.html` | Standalone checklist | Identify |
| `tools/blog-converter.py` | MD → HTML blog pipeline | — |
| `blog/_drafts/` | Yayın öncesi taslaklar | — |
| `blog/[slug]/index.html` | Canlı blog yazıları | — |

## Hızlı Referans — Sorun Giderme

| Durum | Eylem |
|-------|-------|
| QA FAIL | Düzelt → tekrar tara → PASS olmadan devam etme |
| `git push --force` | YASAK |
| Toplu dosya silme | YASAK — tek tek, onay alınarak |
| Deploy görünmüyor | Hard refresh → Cloudflare cache temizle |
| HTML syntax hatası | python3 HTML parser ile tespit et, düzelt |
| CSS token bozulması | `var(--` sayısını commit öncesiyle karşılaştır |
