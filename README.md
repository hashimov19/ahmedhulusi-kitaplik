# site/ — destek ve hukuki sayfalar

Bu klasör **üretilmiş çıktıdır**. Elle düzenleme: metinler `legal/*.md` içinde, sayfaları
üreten araç `tools/site.py`.

```
python tools/site.py
```

## Neden burada bir şablon motoru yok

GitHub Pages isterse Jekyll çalıştırır, ama tema ve permalink davranışı sürprizli olabiliyor.
Bu üç sayfanın App Store ve Play incelemesi sırasında **açılması** gerekiyor; orada bir derleme
hatasını fark etmek için geç olur. Düz HTML her zaman olduğu gibi sunulur. `.nojekyll` dosyası
da Pages'e "derleme, olduğu gibi yayınla" diyor.

## Yayınlama — bir kerelik, ~10 dakika

1. GitHub'da **public** bir depo aç: `hashimov19/ahmedhulusi-kitaplik`
   *(Depo adı URL'in parçası. Değiştirirsen `tools/site.py` çıktısını kullanan üç yerdeki
   adresleri de güncellemek gerekir: `app/src/lib/theme.ts`, `store/*.md`, `KAPILAR.md`.)*
2. Bu klasörün **içindekileri** (klasörün kendisini değil) deponun köküne kopyala —
   `.nojekyll` dahil, o gizli dosya atlanmasın
3. Depo → **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`** → **Save**
4. 1-2 dakika sonra adres açılır:

| Sayfa | Adres |
|---|---|
| Destek (ana sayfa) | `https://hashimov19.github.io/ahmedhulusi-kitaplik/` |
| Gizlilik | `.../gizlilik.html` |
| Kullanım Koşulları | `.../kullanim-kosullari.html` |
| Support (EN) | `.../support.html` |
| Privacy (EN) | `.../privacy.html` |
| Terms (EN) | `.../terms.html` |

## Güncelleme

`legal/*.md` dosyasını düzenle → `python tools/site.py` → `site/` içeriğini depoya kopyala →
commit. Pages birkaç dakika içinde yeniler.

## Uygulamadaki bağlantılar

Ayarlar ekranının alt kartında **Destek ve sık sorulanlar** ile **Gizlilik politikası**
satırları bu adreslere gidiyor (`app/src/lib/theme.ts` → `SUPPORT_URL`, `PRIVACY_URL`,
`PRIVACY_URL_EN`). Gizlilik bağlantısı uygulama diline göre Türkçe veya İngilizce sayfayı açar.
