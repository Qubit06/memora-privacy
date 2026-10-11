# Memora ilk sürüm — yayın öncesi doğrulama

Hedef: QuBit tarafından yayımlanan Memora; ücretsiz en fazla 10 aktif hatırlatma, tek seferlik ve kalıcı Memora Unlimited (`memora_unlimited`). Billing entegrasyonu tamamlanmamıştır. Bu belge uygulama davranışının doğrulandığı anlamına gelmez.

## Billing entegrasyonu

- [ ] Flutter Billing paketi, sürümü ve geçişli Android SDK’ları listelendi; gerçek yayın APK/AAB’si incelendi.
- [ ] Ürün Play Console’da tek seferlik, kalıcı hak sağlayan ürün olarak tanımlandı; abonelik veya yenileme yok. Kalıcı hakkın tüketilerek kaybolmadığı kontrol edildi.
- [ ] Gerçek alınan alanlar belgelendi: ürün kimliği, durum, purchase token, işlem/sipariş kimliği, makbuz/imza, zaman bilgisi gibi alanların hangileri gerçekten işleniyor? Örnekler olası alanlardır; kullanıldıkları varsayılmamalı.
- [ ] Her alanın amacı, bellekte veya diskte tutulması, loglara girmesi, saklama/silme davranışı ve yedeklere dahil olup olmaması belirlendi.
- [ ] Cihaz → Google Play → varsa geliştirici veya üçüncü taraf doğrulama sunucusu veri akışı çıkarıldı. Politika, gerçek alıcı ve işleme davranışlarına göre sonlandırıldı; sunucu yokluğu doğrulanmadan kesinleştirilmedi.
- [ ] Bekleyen, başarılı, başarısız, iptal edilen ve iade edilen işlemler denendi; doğrulama ve acknowledgement tamamlanmadan yanlış hak verilmediği kontrol edildi.
- [ ] Aynı Google Play hesabıyla yeniden başlatma, veri temizleme, yeniden kurulum ve farklı cihaz testleri yapıldı. Farklı hesap ve çevrimdışı durum denendi; destek metnine gerçek geri yükleme adımları yazıldı.
- [ ] 10 aktif hatırlatma sınırı, Unlimited etkinleşmesi, yerel hak önbelleği ve iade sonrası hak davranışı doğrulandı.
- [ ] Kart numarası, güvenlik kodu veya banka şifresinin Memora tarafından doğrudan alınmadığı/saklanmadığı kontrol edildi.

Teknik referans: [Google Play Billing entegrasyonu](https://developer.android.com/google/play/billing/integrate). Bu belge bir Billing mimarisi seçmez ve yeni backend eklemez.

## Google Play Data Safety kontrol listesi

Aşağıdaki liste form için kesin cevaplar vermez. Gerçek APK/AAB, SDK belgeleri ve ağ akışlarıyla doldurulmalıdır. [Google’ın Data Safety rehberi](https://support.google.com/googleplay/android-developer/answer/10787469), geliştirici ve SDK davranışlarının birlikte değerlendirilmesini gerektirir.

- [ ] Cihaz dışına çıkan her satın alma alanı ve alıcısı belirlendi; **Financial info → Purchase history** kategorisinin uygulanabilirliği incelendi.
- [ ] Doğrulama token’ları ve kimliklerin diğer veri kategorilerine girip girmediği gerçek kullanımına göre değerlendirildi.
- [ ] “Toplanan” ve “paylaşılan” ayrımı ile hizmet sağlayıcı/kullanıcı başlatımlı aktarım istisnaları ayrı incelendi; Google Play kullanımı otomatik olarak “veri yok” cevabına dönüştürülmedi.
- [ ] Her kategori için amaçlar (uygulama işlevi, dolandırıcılığı önleme/güvenlik gibi), isteğe bağlı/zorunlu olma ve geçici işleme durumu kanıtlandı.
- [ ] Yalnız cihazda işlenen yerel veriler ile cihaz dışına aktarılan veriler ayrıldı; ses sağlayıcısı ve tüm SDK’lar ayrıca incelendi.
- [ ] Aktarım şifrelemesi ve silme talebi cevapları gerçek teknik/operasyonel davranışla desteklendi. Yerel veri temizlemek Google Play ödeme kayıtlarını silmez.
- [ ] Destek e-postalarının uygulama içi/harici akışı, form kapsamı, saklama ve silme süreci ayrıca değerlendirildi.
- [ ] Form, TR/EN politika, mağaza açıklaması ve yayımlanacak sürüm aynı veri akışını anlatıyor.

## Diğer açık noktalar

- [ ] Android sistem yedekleme ve cihaz aktarımı: manifest ve extraction rules doğrulandı.
- [ ] Mikrofon yalnız sesle yazmada isteniyor; cihaz/uzak sağlayıcı davranışı ve olası ses saklama incelendi.
- [ ] Hatırlatma silme/veri temizleme/kaldırma davranışı, ek dosyalar ve bildirim/kesin alarm izinleri denendi.
- [ ] Destek posta kutusu erişilebilir. Destek mesajlarının **saklama süresi veya saklama ölçütleri**, erişim yetkileri ve silme süreci netleştirildi; politikaya uydurma süre eklenmedi.
- [ ] Hedef yaş grubu ve çocuk gizliliği gereklilikleri belirlendi; politika olmayan bir kayıt sürecinden bahsetmiyor.
- [ ] QuBit adı, iletişim sorumlusu, politika tarihi ve iki dilin eşdeğerliği onaylandı.
- [ ] Yayın sonrası kalıcı URL’ler ve HTTPS kontrol edildi.

Ödeme uyuşmazlıkları için [Google Play iade politikası](https://support.google.com/googleplay/answer/2479637); gizlilik için [Google Gizlilik Politikası](https://policies.google.com/privacy). Bölgeye veya işleme göre değişen iade süresi/garantisi siteye sabitlenmedi.
