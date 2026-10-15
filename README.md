# Nasse Biology

Mavi-lacivert-yeşil temalı, mobil uyumlu biyoloji öğrenme sitesi başlangıç projesi.

## İçerik
- 9, 10 ve 11. sınıf konu bölümleri
- Sketchfab üzerinden etkileşimli 3B beyin, hayvan hücresi, nöron ve omurga/omurilik bölgesi modelleri
- Türkçe yapı bilgi kartları
- Çoktan seçmeli görevler, puan sistemi ve bağlam laboratuvarı
- Firebase Google ile giriş ve e-posta/şifre ile kayıt-giriş için hazır bağlantı alanı
- GitHub Pages ile yayınlanabilir statik dosyalar

## 1. VS Code'da açma
1. ZIP dosyasını çıkar.
2. VS Code'da `nasse_biology` klasörünü aç.
3. `index.html` dosyasını doğrudan çift tıklamak yerine Live Server benzeri bir yerel sunucu uzantısıyla aç. ES modülleri nedeniyle `file://` adresinden açmak sorun çıkarabilir.
4. `index.html`, `style.css`, `app.js` ve `firebase-config.js` aynı klasörde kalmalı.

## 2. Firebase girişini kurma
1. https://console.firebase.google.com adresinde proje oluştur.
2. Proje ayarlarından bir Web uygulaması ekle ve yapılandırma değerlerini al.
3. `firebase-config.js` içindeki `apiKey`, `authDomain`, `projectId` ve `appId` alanlarını gerçek değerlerle değiştir.
4. Firebase Console > Authentication > Sign-in method bölümünde **Google** ve **E-posta/Şifre** yöntemlerini etkinleştir.
5. Authentication ayarlarında yetkili alan adlarına yerel geliştirme için `localhost`, GitHub Pages için örneğin `eliffrkk45-jpg.github.io` alan adını ekle. Alan adına `https://` veya `/nasse/` yolunu ekleme.
6. Siteyi yeniden yükle. Google girişi mobil uyumlu yönlendirme kullanır.

Firebase istemci yapılandırması tek başına yetkilendirme değildir. Kullanıcı verisi saklamaya başlarsan Firestore kullan ve güvenlik kurallarını ayrıca yaz.

## 3. GitHub Pages ile yayımlama
1. Dosyaları GitHub deposunun kök dizinine yükle.
2. Depoda Settings > Pages bölümüne gir.
3. Build and deployment altında `Deploy from a branch` seç.
4. `main` dalı ve `/(root)` klasörünü seçip kaydet.
5. Yayın adresin `https://KULLANICI.github.io/DEPO-ADI/` biçiminde olur.
6. Firebase Authentication > Authorized domains alanına `KULLANICI.github.io` alan adını ekle.

## 4. 3B modeller ve atıf
Modeller Sketchfab gömülü görüntüleyicisiyle açılır. Görüntüleyici desteklediği ölçüde fare veya dokunmatik hareketlerle döndürme ve yakınlaştırma sağlar.

- Beyin: FrankJohansson, “Human brain, Cerebrum & Brainstem”, CC BY. Model sayfası: https://sketchfab.com/3d-models/human-brain-cerebrum-brainstem-0aa0e33c5c854d1bab7bac9e1c7acaec
- Hayvan hücresi: montanna, “Animal cell 2.0 - annotated in English”, CC Attribution. Model sayfası: https://sketchfab.com/3d-models/animal-cell-20-annotated-in-english-0d9f7f4257224975b2ef83a283709b2f
- Nöron: https://sketchfab.com/3d-models/neuron-for-psy150-d2a2dedec2f846cf9a04cb1969e40782
- Omurga: https://sketchfab.com/3d-models/the-human-spinal-column-bcd9eee09ce044ef98a69c315aa792e2

Yayımlamadan önce her modelin güncel lisansını ve atıf koşullarını model sayfasından yeniden kontrol et. Gömülü görüntüleyicinin kullanımı, modeli parçalara ayırıp ayrı ayrı seçme yeteneği sağlamaz. Türkçe bilgi kartları bu başlangıç sürümünde ayrı etkileşimli kartlardır.

## 5. Önemli notlar
- Bu proje çalıştırılabilir bir başlangıç sürümüdür; tüm Maarif Modeli kazanımlarının resmî eşleştirmesi ve ders içeriklerinin öğretmen tarafından kontrol edilmesi gerekir.
- Puanlar şu anda tarayıcının `localStorage` alanında tutulur. Başka cihazlarda görünmez; bunun için Firestore entegrasyonu gerekir.
- Model sayfaları internet bağlantısı ister. Bir modelin sahibi onu kaldırır veya gömmeyi kapatırsa başka bir model seçilmelidir.
- Firebase yapılandırma değerlerini eklemeden giriş düğmeleri gerçek kimlik doğrulama yapamaz.


## Güncelleme: konu anlatımları ve Türkçe etkileşim
- Hızlı görev havuzu 30 soruya çıkarıldı.
- Sınıf konularına tıklanınca Türkçe konu anlatımı ve ilgili 3B modeli açma bağlantısı gösterilir.
- Sketchfab model URL'lerinde desteklendiği ölçüde model yükleyicisinin ek açıklamaları kapatılmaya çalışılır (`ui_annotations=0`). Böylece model sahibinin İngilizce açıklamalarının görünmesi azaltılabilir.
- Önemli sınır: Sketchfab içindeki modelin kendi açıklama metinleri yükleyen tarafından hazırlanır ve bunları sayfanın JavaScript koduyla Türkçeye çevirmek mümkün değildir. Bu nedenle Türkçe bilgi kartları site içinde hazırlanmıştır. Eğer model üzerindeki İngilizce etiketler hâlâ görünüyorsa modelin kendi anotasyonları bu ayarı dikkate almıyor olabilir; o durumda bu modeli etiketleri kapatılmış biçimde kullanmak veya lisansı izin veren indirilebilir bir 3B dosyayı Türkçe etkileşimlerle yeniden hazırlamak gerekir.

## Bu sürümdeki öğrenme ve 3B güncellemeleri

- 9., 10. ve 11. sınıf seçildiğinde o düzeye özel konu başlıkları, konu anlatımı kartları ve ayrı bir soru seti açılır.
- Her sınıfın soru setinde 7–8 soru bulunur; doğru cevap geri bildirimi açıklamayla birlikte gösterilir.
- Son aşamadaki Bağlam Laboratuvarı sınıflar arası bağlantı kuran senaryoları içerir.
- Mevcut Sketchfab modellerinin bağlantıları ve modelleri değiştirilmedi. Modelin İngilizce gömülü adlarını/mesh isimlerini uygulama kodundan güvenilir biçimde yeniden adlandırmak mümkün olmadığı için bunları Türkçeye çevirdiğimizi iddia etmiyoruz. Sayfa içinde seçilen modele göre ayrı Türkçe anatomik yapı kartları gösterilir; bu kartlar bilgi panelini değiştirir.
- Türkçe yapı kartları, modelin içindeki gerçek geometriyi otomatik olarak seçip renklendirmez. Bu tür doğrudan mesh seçimi için model dosyalarının düzenlenebilir/indirilebilir sürümü ve lisansı uygun olmalı, ardından Three.js ile siteye yerel olarak eklenmelidir.
- GitHub Pages'te mevcut siteyi güncellemek için ZIP içindeki dosyaları proje deposundaki karşılıklarıyla değiştir. `firebase-config.js` dosyandaki kendi Firebase ayarlarını koru.
