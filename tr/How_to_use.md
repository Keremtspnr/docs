# Kullanım Talimatları

**Önemli! Talimatları baştan sona okuduktan sonra çalışmaya başlayın! İyi şanslar!**

## Nasıl Çalışır?

Öncelikle projeyi indirmeniz gerekecek. ***instabot/examples/*** klasörünün içerisinde scriptin çalıştırabileceğiniz dosyaları bulunmaktadır.

## Scriptleri nasıl çalıştırabilirim?

Komut satırını açıp, ***cd*** komutunu kullanarak proje klasörüne (***instabot/examples***) erişin ve yazın.

``` python
python name.py param
```

***name*** yerine çalıştırmak istediğiniz scripti yazın, ***param*** ise gerekli parametreleri tanımlamanız gereken kısım. Her scriptte parametre girmenize gerek yoktur. 

## Scriptin parametreye ihtiyaç duyup duymadığını nasıl anlarım?

Önce scripti çalıştırın.

``` python
python name.py
```
Eğer gerekli bir parametre girilmemiş ise, script durdurulacak ve size bir hata gösterecektir.
Örneğin: 
Scripti çalıştırın.

``` python
python like_hashtags.py. 
```

Script durdurulacak ve hata mesajı gözükecek.

``` python
error: the following arguments are required: hashtags.
```

Yani, bir hashtag girmek zorunda kaldık. Doğru örnek:

``` python
python like_hashtags.py follow
```

## Herşey Dahil

***multi_script_CLI.ph*** scripti tüm fonksiyonları içeren bir scripttir. İlk çalıştırdığınız zaman, sizden bir konfigurasyon istenecektir. Script ayarları ***setting.txt*** dosyası içerisinde saklanır. Ayrıca ***hashtag_file.txt, users_file.txt, whitelist.txt, blacklist.txt, comment.txt*** dosyaları da oluşturulacaktır.

## 7/24 Çalışır 

Evet, belirli kişilerin abonelerini ve aboneliklerini 24 saat boyunca takip eden bir senaryo var, ayrıca nickname ve hashtag'e göre fotoğrafları beğenir. Bütün bunlar ***ultimate.py*** scriptinde yer alır ***instabot/examples/ultimate*** klasöründe.
Bu klasör aynı zamanda scripti çalıştıracak diğer text dosyalarını da içerir. Bu dosyalar içinde, ihtiyaç duyulan her yeni parametre, yeni satıra yazılmalıdır. 

## Zamanlama Yapmak

Ayrıca zamanlayarak çalıştırabileceğiniz scriptte mevcuttur. ***instabot/examples/ultimate_schedule*** klasörü içerisinde ***ultimate.py*** scriptini kullanmanız gerekmektedir. Bu scripti herhangi bir kod editör ile açıp düzenlemeniz gerekmektedir. Çok kolay ve zahmetsiz bir işlemdir, sorun yaşamayacaksınız. 

## Scripti nasıl doğru konfigüre edebilirim

Hesabınızın yasaklanmadığından emin olmak için Örnek betiğini yapılandırmanız gerekir. Belirli bir hashtagdeki fotoğrafları her dakika kontrol ettiğimizi varsayalım. Her şeyden önce, zamanı saniye cinsinden kontrol edeceğiz. Herhangi bir editör ile ***like_hashtags.py*** dosyasını açın. Bu tür satırlar bulun (Aşağı yukarı benzer olacaklardır).

``` python
bot = Bot()
bot.login(username=args.u, password=args.p,
          proxy=args.proxy)
```

Sonraki satırda.

``` python
bot = Bot()
```

Parantez içine bir parametre yazmamız gerekiyor. Bu parametre *** like_delay *** şeklindedir. Bu parametrenin 60 olarak ayarlanması gerekiyor, çünkü botun hashtag'deki fotoğrafı beğenmesi için her 1 dakikaya ihtiyacımız var. Sonunda, bu gibi görünecek.

``` python
bot = Bot(like_delay=60)
bot.login(username=args.u, password=args.p,
          proxy=args.proxy)
```

## Parametre Listesi

| Parametre | Açıklama | Örnek |
| ------------- |:-------------:| ------:|
| proxy | Instabot için proxy | None|
| max_likes_per_day| Bot günde kaç beğeni gönderebilecek | 1000|
| max_unlikes_per_day | Bot günde kaç gönderiyi unlike edebilecek | 1000|
| max_follows_per_day| Günlük maksimum follow etme sayısı | 350|
| max_unfollows_per_day| Günlük maksimum unfollow etme sayısı | 350|
| max_comments_per_day| Günlük yorum yapma sayısı | 100|
| max_likes_to_like| Eğer gönderi bu sayıdan daha fazla beğeniye sahip ise - onu yok sayacak ve beğenmeyecek | 200|
| filter_users | Kullanıcı filtreleme açıp kapatma | True|
| max_followers_to_follow| Eğer kullanıcı bu sayıdan daha fazla takipçiye sahip ise - onu yok sayacak ve takip isteği veya beğeni göndermeyecek. | 2000|
| min_followers_to_follow| Eğer kullanıcı bu sayıdan daha az takipçiye sahip ise - onu yok sayacak ve takip isteği veya beğeni göndermeyecek.| 10|
| max_following_to_follow| Eğer kullanıcı bu sayıdan daha fazla takip eden sayısına sahip ise - onu yok sayacak ve takip isteği veya beğeni göndermeyecek.| 10000|
| min_following_to_follow| Eğer kullanıcı bu sayıdan daha az takip eden sayısına sahip ise - onu yok sayacak ve takip isteği veya beğeni göndermeyecek.| 10|
| max_followers_to_following_ratio| Eğer kullanıcının takipçi / takip oranı bu sayıdan fazla ise - onu yok sayacak ve takip isteği veya beğeni göndermeyecek. | 10|
| max_following_to_followers_ratio| Eğer kullanıcının takip / takipçi oranı bu sayıdan fazla ise - onu yok sayacak ve takip isteği veya beğeni göndermeyecek.| 2|
| min_media_count_to_follow| Eğer kullanıcının bu sayıdan daha az gönderi sayısı var ise - onu takip etmeyecek. | 3|
|max_following_to_block|Eğer kullanıcının bu sayıdan daha fazla takipçisi var ise - onu takip etmeyecek ve bloklayacak. Çünkü bu sayfa bir kitle sayfası olabilir.| 2000|
| max_likes_to_like | Gönderiyi beğenmek için, sahip olması gereken maksimum beğeni sayısı. | 100 |
| like_delay | Beğeniler arasındaki bekleme süresi (saniye) | 10|
| unlike_delay | Beğeni kaldırma arasındaki bekleme süresi (saniye) | 10|
| follow_delay | Follow yapma arasındaki bekleme süresi (saniye) | 30|
| unfollow_delay | unFollow yapma arasındaki bekleme süresi (saniye) | 30|
| comment_delay | Yorum yapma arasındaki bekleme süresi (saniye) |  60|
| whitelist | Takipten çıkarılmaması gereken kullanıcı listesi | "whitelist.txt"|
| blacklist | Takip edilmemesi, beğenilmemesi ve yorum yapılmaması gereken kullanıcıların listesi | "blacklist.txt"|
| comments_file | Yorum listesi veritabanı | "comments.txt" |
| stop_words| Dikkat edilecek kelimeler. Bu kelimelerin yer aldığı açıklama kısımlarına sahip kullanıcıları takip etme. | ['shop', 'store', 'alışveriş']|























