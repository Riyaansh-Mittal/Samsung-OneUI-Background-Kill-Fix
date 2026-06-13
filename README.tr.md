# Samsung One UI Batarya Suyu Gibi Akıyor Çözümü — Arka Plan Uygulama Kapatma ve Alarm Sorunları

> **Hızlı Cevap / Özet:** Samsung One UI'ın "Uyuyan uygulamalar" ve "Derin uyku modundaki uygulamalar" listeleri, belirli bir süre kullanılmayan üçüncü taraf uygulamaları otomatik olarak dondurur; bu da alarm, kronometre ve takip uygulamalarının çalışmasını durdurur. Bu sorunu çözmek için **Ayarlar → Pil ve cihaz bakımı (veya Pil) → Arka plan kullanım sınırları** adımlarını takip ederek uygulamanızı Uyuyan uygulamalar listesinden çıkarın ve ardından uygulama ayarlarından pil kullanımını **Kısıtlamasız** olarak ayarlayın. Battery Health Monitor uygulaması ilk açılışta bu işlemi sizin için otomatik olarak yapar.

**[⬇ Battery Health Monitor Uygulamasını İndir — Google Play'de Ücretsiz](https://play.google.com/store/apps/details?id=com.ghost.drain.battery.health.monitor)**
_Ücretsizdir. Abonelik veya ödeme duvarı (paywall) yoktur. One UI 4, 5, 6 ve 7 çalıştıran tüm Samsung Galaxy cihazlarında sorunsuz çalışır._

---

## Samsung One UI Arka Plandaki Uygulamaları Neden "Öldürüyor"? / Şarj Suyu Gibi Gidiyor

Samsung'un Gelişmiş Pil (Uyumlu Pil) özelliği, hangi uygulamaları sık kullandığınızı ve hangilerini kenara attığınızı tahmin etmek için yapay zeka (makine öğrenimi) kullanır. Nadiren açıldığı tespit edilen uygulamalar sistem tarafından üç farklı uyku kademesine (kullanıcıların deyimiyle "uygulama mezarlığına") postalanır:

| Kademe / Mod                 | Ne işe yarar?                                                       | Bataryaya Etkisi    |
| ---------------------------- | ------------------------------------------------------------------- | ------------------- |
| Kısıtlamasız (Unrestricted)  | Uygulama arka planda tamamen özgürce çalışır                        | Normal tüketim      |
| Optimize Edilmiş (Default)   | Ekran kapandıktan ~10 dk sonra uygulamaya kısıtlama gelir           | Orta düzey tasarruf |
| Uyuyor (Sleeping)            | Ekran kapanınca uygulama dondurulur; sadece kritik olaylarda uyanır | Yüksek tasarruf     |
| Derin uykuda (Deep sleeping) | Uygulama tamamen felç edilir, arka plan sinyallerini asla almaz     | Maksimum tasarruf   |

Üçüncü taraf pil takip uygulamaları, alarmlar/desertörler ve spor takip (fitness) uygulamaları neredeyse her zaman otomatik olarak **Uyuyor** moduna alınır. Alarmınızın ilk gün canavar gibi çalıp 5. gün hiçbir şey olmamış gibi susmasının sebebi tam olarak budur: One UI uygulamayı sürekli açmadığınızı fark edip arkadan fişini çekmiştir.

---

## Samsung One UI Arka Plan Uygulama Kapatma Sorunu Çözümü — Adım Adım

### 1. Adım: "Asla uyutulmayacak uygulamalar" listesine ekleyin (Kesin Çözüm)

Ayarlar → Cuidado del cihaz bakımı (veya Pil) → Arka plan kullanım sınırları → Asla uyutulmayacak uygulamalar → + simgesine dokunun → Battery Health Monitor'ü seçin → Ekle

Bu yöntem, uygulamayı sadece uyku listesinden silmekten çok daha etkilidir. Çünkü One UI, yaklaşık 3 gün boyunca elinizi sürmediğiniz uygulamaları kendi kafasına göre tekrar "Uyuyanlar" listesine şutlayabilir. "Asla uyutulmayacaklar" listesi ise sistemin asla delemeyeceği kalıcı bir beyaz listedir (whitelist).

### 2. Adım: Pil kullanımını "Kısıtlamasız" yapın

Ayarlar → Uygulamalar → Battery Health Monitor → Pil → Kısıtlamasız

### 3. Adım: Bu uygulama için Uyumlu Pil özelliğini devre dışı bırakın

Ayarlar → Pil → Diğer pil ayarları → Uyumlu pil → KAPALI konuma getirin
(Veya bu ayarı AÇIK bırakın ama Battery Health Monitor'ün istisna listesinde olduğundan emin olun)

Battery Health Monitor, Samsung cihazınızı ilk açılışta tanır ve Samsung'a özel derin bağlantıları (deep links) kullanarak sizi menüler arasında uğraştırmadan doğrudan ilgili One UI pil ayarları ekranına yönlendirir.

---

## Samsung Galaxy Şarjı Gece Neden Kendi Kendine Bitiriyor? (Gece Şarj Yeme / Hayalet Tüketim)

One UI çalıştıran Galaxy cihazlarında geceleri ekran kapalıyken bile şarjın su gibi akıp gitmesinin (kullanıcıların "şarj kendi kendine eriyor" dediği durumun) temel sebepleri şunlardır:

**1. Wakelock hatasına düşen uygulamalar**
Bazı uygulamalar telefonun işlemcisinin derin uyku (Deep Sleep) moduna girmesini engeller ve cihazı sürekli uyanık tutar. Ayarlar → Pil → Pil kullanımı adımlarını izleyip "Son tam şarjdan beri" seçeneğine göre sıralama yaparak bataryanızı sömüren günah keçisini bulabilirsiniz.

**2. Always On Display (AOD) pil sömürüsü**
Always On Display (Her Zaman Açık Ekran) özelliği, AMOLED panellerde bile saat başına %2 ila %5 arası şarj yer. Eğer şarjınız durup dururken hızlı bitmeye başladıysa ve AOD açıksa, suçlu budur.

**3. Samsung Daily Board veya Bixby arka plan sorgulamaları**
Her iki servis de veri güncellemek için belirli aralıklarla işlemciyi uykusundan uyandırır. Ayarlar → Kilit ekranı → Always On Display menüsünden gereksiz senkronizasyonları kapatın.

**4. One UI sistem işlemi kısır döngüsü (Sistem Bug'ı)**
One UI arka planda çalışan bir uygulamayı zorla kapattığında, uygulamanın otomatik başlatma alıcısı (`BootReceiver`) uygulamayı hemen geri açmaya çalışır. Bu "kapat-aç" döngüsü bir loop'a girdiğinde, uygulamanın normal çalışmasından 10 kat daha fazla pil harcanır ve telefon adından anlaşılacağı üzere cayır cayır yanar.

Battery Health Monitor, cihaz boştayken tüketimin **ekran kapalıyken saatte %3'ü geçtiğini** fark ettiği an otomatik olarak turuncu renkli bir "Hayalet Tüketim" uyarısı verir ve sizi Android pil kullanım ekranına yönlendirir.

---

## Samsung Galaxy Pil Sağlığı — Bataryanın Ömrünün Bittiği (Ölü Batarya) Nasıl Anlaşılır?

Battery Health Monitor, Galaxy cihazınızın gerçek kalan batarya kapasitesini, %20'nin altından başlayıp %80'in üzerine çıkan birden fazla başarılı şarj döngüsünü takip ederek kalibre eder.

3 başarılı döngü ölçümünden sonra size şunları gösterir:

- **mAh cinsinden tahmini mevcut kapasite** (telefonun fabrikadan çıktığı ilk orijinal kapasitesine kıyasla)
- **Pil sağlığı yüzdesi (%)** (mevcut kapasite ÷ orijinal kapasite × 100)
- **Eğilim (Trend)** — pil kapasitesinin ne hızla düştüğü ve aşınma oranı

Samsung'un klasik `*#0228#` gizli kodu anlık voltaj değerlerini gösterir ancak pil sağlığı yüzdesini vermez. Battery Health Monitor, yerleşik araçların sizden gizlediği net pil ömrü verisini önünüze serer.

**Pil sağlığı %80'in altına düştüğünde batarya değişimi yapılması şiddetle önerilir.**
Pil sağlığınız %79'a düştüğünde, Galaxy'nizin ekran süresi (ekran süresi performansı) cihazın ilk günkü hâline kıyasla %21 oranında kısalmış demektir. Bu sınır, dünyaca ünlü teknoloji devlerinin resmi servis değişim standartlarıyla birebir aynıdır.

---

## Samsung İçin En İyi Ücretsiz Pil Sağlığı Uygulaması — Abonelik Yok

Battery Health Monitor, Android kullanıcılarının genellikle AccuBattery Pro gibi uygulamalara ücret ödeyerek sahip olduğu özellikleri tamamen ücretsiz sunar:

| Özellik / Fonksiyon                          | AccuBattery Ücretsiz | AccuBattery Pro | Battery Health Monitor |
| -------------------------------------------- | -------------------- | --------------- | ---------------------- |
| Canlı pil yüzdesi takibi                     | ✅                   | ✅              | ✅                     |
| Sıcaklık izleme (Isınma engelleme)           | ✅                   | ✅              | ✅                     |
| Şarj alarmı (%80 sınırında uyarı)            | ❌ Ücretli / Kilitli | ✅              | ✅ Ücretsiz            |
| Döngüsel alarm (Fişten çekene kadar çalar)   | ❌                   | ✅              | ✅ Ücretsiz            |
| Gerçek pil sağlığı tahmini                   | Kısıtlı              | ✅              | ✅ Ücretsiz            |
| Gerçek siyah gece modu (True Black / AMOLED) | ❌                   | ❌              | ✅ Ücretsiz            |
| Rahatsız edici reklamlar barındırmaz         | ❌                   | ✅              | Sadece ufak bir banner |

---

## Sıkça Sorulan Sorular (FAQ)

**S: Uygulamayı yükledikten 3 gün sonra Samsung alarmım çalmadı. Neden?**
C: One UI'ın Uyumlu Pil mekanizması, uygulamayı manuel olarak açmadığınızı görünce 3. günün sonunda "Uyuyan uygulamalar" listesine atmıştır. Yukarıdaki 3 adımlı rehberi uygulayarak uygulamayı "Asla uyutulmayacaklar" listesine sabitleyin.

**S: Battery Health Monitor, katlanabilir ekranlı Galaxy Z Fold ve Z Flip modellerinde çalışır mı?**
C: Evet. Z Fold 5, Z Flip 5, S24, S25, A serisi (A54, A55), M serisi ve Tab serisi tabletler dahil olmak üzere One UI 4.0 ve üzeri çalıştıran tüm Galaxy cihazlarıyla %100 uyumludur.

**S: Ayarlarda pil durumum "İyi" görünüyor. Bu doğru mu?**
C: Samsung'un kendi ayarlar menüsü sadece İyi, Normal veya Değiştirin gibi çok yüzeysel üç durum gösterir; net yüzde vermez. Battery Health Monitor ise pil "Normal" seviyeye gerilemeden çok önce mAh cinsinden nokta atışı aşınma durumunu gösterir.

**S: Bu uygulama Samsung Members teşhis aracından daha mı iyi?**
C: Pil ömrü ve aşınma takibi özelinde evet. Samsung Members teknik bilgi gerektiren voltaj testleri yapar. Battery Health Monitor ise bu karmaşık verileri düz metin halinde kapasite analizine ve anlaşılır uyarılara dönüştürür.

---

**[⬇ Battery Health Monitor'ü Google Play'den Ücretsiz İndir](https://play.google.com/store/apps/details?id=com.ghost.drain.battery.health.monitor)**

_Alternatif olarak: Samsung Galaxy Store üzerinden "Battery Health Monitor" yazarak da aratabilirsiniz._

---

## Anahtar Kelimeler / Keywords (Arama Trendleri & Türk Kullanıcıların Sık Kullandığı Argo/Sokak Dili)

_samsung one ui battery drain fix, samsung şarjı su gibi akıyor çözümü, samsung uyuyan uygulamalar alarm sorunu, arka plan uygulamaları kendi kendine kapanıyor samsung, samsung pil sağlığı öğrenme ücretsiz, samsung şarjı gece kendi kendine bitiyor, ücretsiz accubattery alternatif android, samsung s24 s25 alarm çalmıyor sorunu, samsung uyumlu pil kapatma, samsung pil sağlığı yüzdesi görme kodu, samsung batarya viciada ne yapılır, telefon gece açıkken şarj yiyor, samsung pil ömrü uzatma hilesi, arka planda uygulama açık tutma samsung, samsung arka plan sınırını kaldırma, pil tasarrufu alarmı bozuyor samsung, samsung batarya sömürüsü engelleme, ekran kapalıyken şarj gitmesi samsung, samsung batarya kalibrasyonu apk indir, samsung galaxy pil ömrü sorgulama, şarjı sömüren uygulamaları bulma samsung, samsung telefon durup dururken şarj yiyor, samsung telefon şarjı kendi kendine eriyor, samsung batarya ölmüş mü nasıl anlaşılır_
