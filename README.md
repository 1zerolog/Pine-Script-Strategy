# Pine Script Strategy Template

TradingView Pine Script v6 icin hazirlanmis strateji sablonu.

Bu repo, yeni stratejiler gelistirirken tekrar tekrar kullanilabilecek temel bir Pine Script iskeleti sunar. Long/short giris kosullari bilincli olarak bos birakilmistir; kullanici kendi trend, sinyal veya filtre mantigini `TREND-STRATEGY`, `MAIN-STRATEGY` ve `FINAL_CONDITIONS` alanlarina ekleyerek stratejiyi tamamlar.

## Dosyalar

- `Template/Template.pine`: TradingView Pine Script v6 strateji dosyasi.
- `Template/Template.txt`: Ayni stratejinin metin kopyasi / referans surumu.

## Ozellikler

- Pine Script v6 strateji yapisi
- Long ve short islemleri acip kapatma secenekleri
- Backtest tarih araligi filtresi
- Kaldirac ve equity yuzdesine gore pozisyon miktari hesaplama
- Long/short icin ayri alarm/comment ID alanlari
- Ortalama pozisyon fiyatina gore TP ve SL hesaplama
- TP/SL tetiklerinde tek seferlik market close mantigi
- Long ve short icin trailing stop close sistemi
- Pyramiding veya pozisyon ekleme durumunda TP/SL state reset mantigi

## Kullanim

1. `Template/Template.pine` dosyasini TradingView Pine Editor icine yapistirin.
2. `TREND-STRATEGY` ve `MAIN-STRATEGY` bolumlerine indikatorlerinizi veya sinyal mantiginizi ekleyin.
3. `FINAL_CONDITIONS` bolumunde `enterLong` ve `enterShort` kosullarini tanimlayin.
4. Backtest, leverage, TP/SL ve trailing stop ayarlarini TradingView input panelinden duzenleyin.

Ornek final kosul yapisi:

```pine
enterLong  = longSignal and trendUp
enterShort = shortSignal and trendDown
```

## Ana Ayarlar

| Ayar | Aciklama |
| --- | --- |
| `Backtest` | Tarih filtresini aktif/pasif yapar. |
| `Start` / `End` | Backtest tarih araligini belirler. |
| `Enter Long Position` | Long girislerini aktif eder. |
| `Enter Short Position` | Short girislerini aktif eder. |
| `LEVERAGE (%)` | Equity'nin kullanilacak yuzdesini belirler. |
| `LEVERAGE (X)` | Pozisyon miktari hesabinda kullanilan kaldirac katsayisi. |
| `TP %` | Ortalama pozisyon fiyatina gore kar alma yuzdesi. |
| `SL %` | Ortalama pozisyon fiyatina gore zarar durdurma yuzdesi. `0` yapilirsa SL kapatilir. |
| `Trail Point %` | Trailing stop'un aktif olacagi fiyat mesafesi. |
| `Trail Offset %` | Trailing stop aktif olduktan sonra takip mesafesi. |

## Notlar

- Bu dosya dogrudan calisan nihai bir stratejiden cok, strateji gelistirmek icin baslangic sablonudur.
- `enterLong` ve `enterShort` satirlari doldurulmadan Pine Editor hata verebilir.
- Varsayilan komisyon `0.1%`, baslangic sermayesi `100 USD`, pozisyon tipi ise equity yuzdesi uzerinden ayarlanmistir.
- Gercek piyasada kullanmadan once farkli sembol, zaman dilimi ve piyasa kosullarinda ayrintili backtest yapilmalidir.

## Uyari

Bu repo yatirim tavsiyesi degildir. Strateji sablonu egitim, test ve gelistirme amaciyla paylasilmistir. Canli islemlerde kullanmadan once risk yonetimi, slipaj, komisyon ve piyasa kosullari mutlaka dikkate alinmalidir.
