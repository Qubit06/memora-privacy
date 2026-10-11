# Memora — Gizlilik ve Destek

İki dilli, mobil uyumlu statik GitHub Pages sitesi. Renkler: `#244D3F` ve `#F6F5EF`. Backend, veritabanı, analytics, reklam, harici font ve ücretli servis yoktur. Tarayıcı JavaScript’i, çerez ve localStorage kullanılmaz. Dil bağlantıları ve SSS JavaScript kapalıyken çalışır.

## Dosyalar ve adresler

Yayın tabanı: https://qubit06.github.io/memora-privacy/

| Dosya / yayın tabanına eklenecek yol | Sayfa |
| --- | --- |
| `index.html` | Türkçe ana sayfa |
| `privacy-policy.html` | Türkçe gizlilik politikası |
| `support.html` | Türkçe destek |
| `en/index.html` | English home |
| `en/privacy-policy.html` | English privacy policy |
| `en/support.html` | English support |

Diğer dosyalar: `assets/styles.css` ortak tasarım, `assets/favicon.svg` yerel simge, `.nojekyll` Jekyll’i kapatır, `build-site.cjs` HTML üreticisidir. Göreli bağlantılar `/memora-privacy/` altında çalışır. Dil değişimi aynı sayfanın karşılığına gider.

## Yerel inceleme

Paket kurulumu gerekmez. `index.html` tarayıcıda doğrudan açılabilir. HTTP önizlemesi için Python kuruluysa depo üst dizininde `python -m http.server 8080` çalıştır, `http://localhost:8080/memora-privacy/` adresini aç. Ctrl+C sunucuyu durdurur.

Metinler `build-site.cjs` içinde düzenlenir; depo kökünde `node build-site.cjs` altı HTML dosyasını yeniden üretir. CSS doğrudan düzenlenir. Üretici, HTML’de elle yapılan değişikliklerin üzerine yazar. GitHub Pages hazır HTML’yi sunar; Node veya build çalıştırması gerekmez.

## Yayınlama

1. Dosyaları ve aşağıdaki ürün maddelerini incele.
2. Onaydan sonra dosyaları seçtiğin dala commit edip push et.
3. GitHub **Settings → Pages → Build and deployment → Deploy from a branch** seç.
4. Dosyaların bulunduğu dalı (örneğin `main`) ve **/(root)** klasörünü seç; kaydet.
5. Yayın tamamlanınca altı sayfayı aç ve **Enforce HTTPS** seçeneğini kontrol et.
6. Google Play gizlilik politikası alanında doğrudan `privacy-policy.html` veya `en/privacy-policy.html` adresini kullan.

Bu çalışma sırasında commit, push veya yayın yapılmamıştır. Özel sunucu veya ücretli hizmet gerekmez. GitHub Pages’in barındırma işlemleri uygulamanın yerel veri saklamasından ayrıdır; siteye takip kodu eklenmemiştir.

## Yayın öncesi ürün doğrulaması

Android kaynak kodu bu depoda yoktur; uygulama açıklamaları verilen ürün bilgilerine dayanır. Gerçek yayın sürümünde şu maddeleri doğrula:

- SQLite/Drift alanları, ek dosyalar, saklama ve silme işlemlerinin kapsamı.
- Manifest’te `allowBackup`, `dataExtractionRules`, `fullBackupContent`; sistem yedeği ve cihaz aktarımının kapsamı.
- Bildirim/kesin alarm izinleri, izin reddi ve yeniden başlatma sonrası davranış.
- Mikrofon izninin yalnızca sesle yazma başlatıldığında istenmesi; sağlayıcı ve varsa ses dosyası saklama davranışı.
- Bağımlılıklar ve ağ trafiğinde analytics, crash reporting, telemetri, reklam veya uzak API bulunup bulunmadığı. Doğrulanmadan “hiçbir veri toplanmaz/paylaşılmaz” iddiası ekleme.
- Hesap, giriş, bulut senkronizasyonu, AI ve OCR bulunmaması; ilk sürümde Google Play Billing ile `memora_unlimited` tek seferlik satın alımının etkin olması.
- Destek posta kutusunun erişilebilirliği, mesajların kullanımı, saklama/silme uygulamaları ve iletişim sorumlusu.
- Hedef yaş grubu ve uygulanabilir çocuk gizliliği yükümlülükleri. Doğrulanmış yaş sınırı olmadığı için metinde bir yaş eşiği uydurulmamıştır.
- Politika tarihi, çeviri eşdeğerliği ve Play Data Safety beyanlarının gerçek davranışla tutarlılığı. Yeni özelliklerde politikayı güncelle.

Referanslar: [Android SpeechRecognizer](https://developer.android.com/reference/android/speech/SpeechRecognizer), [Alarmlar](https://developer.android.com/develop/background-work/services/alarms), [Bildirim izinleri](https://developer.android.com/develop/ui/views/notifications/notification-permission).

## İlk yayın sürümü ve Billing

Geliştirici adı **QuBit**. Politika ilk Google Play sürümünde Billing’in etkin olacağı hedef kapsamına göre hazırlandı; uygulama entegrasyonu henüz doğrulanmadı. Ücretsiz sürüm 10 aktif hatırlatma, `memora_unlimited` ise tek seferlik satın alımla kalıcı olarak sınırsız aktif hatırlatma sunar. Abonelik yoktur. Global fiyat sabitlenmemiştir.

TR/EN politika ve destek metinleri birlikte güncellendi. Google Play ödemeleri, uygulamanın doğrudan almadığı kart/banka bilgileri, satın alma durumu ve doğrulama bilgileri, Google Play hesabına bağlı hak kontrolü, internet ihtiyacı ve iade koşulları açıklandı. Yerel silme, Google Play kayıtlarını silmez; destek cihazdaki hatırlatmaları uzaktan silemez. Geri yükleme için henüz olmayan bir düğme veya otomatik cihazlar arası davranış vaat edilmedi.

Yayın öncesi ayrıntılı Billing ve Data Safety kontrol listesi: [RELEASE-CHECKLIST.md](RELEASE-CHECKLIST.md). Gerçek veri alanları, sunucu mimarisi, destek mesajlarının saklama süresi ve silme süreci netleştirilmeden yayın sürümüyle tam uyum iddiasında bulunulamaz.

## Kontrol kapsamı

Billing güncellemesinden sonra altı sayfa Edge tarayıcısında 320, 390, 768 ve 1440 px genişliklerinde yeniden kontrol edildi; yatay taşma bulunmadı. Yerel bağlantılar, dil geçişleri, `mailto:` adresleri, QuBit bilgisi, tek ana başlık, klavye odağı, içerik atlama bağlantısı ve iki dilde dokuz SSS’nin etkileşimi geçti. Yeniden build aynı HTML çıktısını üretti. HTTP veya JavaScript hatası görülmedi. Politikanın masaüstü/mobil ve destek sayfasının mobil ekran görüntüleri incelendi. Gerçek cihazda e-posta uygulamasının açılması cihaz yapılandırmasına bağlıdır. Bu kontroller web sitesini kapsar; Billing entegrasyonunun, Android kaynak kodunun ve yayın sonrası HTTPS’nin doğrulandığı anlamına gelmez.
